# SAP Integration Patterns — Quick Reference

## Connectivity Options (by scenario)

| Scenario | Recommended | Notes |
|---|---|---|
| Read SAP master data (readonly) | OData V4 / RFC via PyRFC | OData preferred if S/4HANA; RFC for ECC |
| Write transactional data | BAPI via RFC | Always use BAPI_TRANSACTION_COMMIT |
| Event-driven (SAP → External) | IDoc outbound / SAP Event Mesh (BTP) | IDoc for ECC; Event Mesh for S/4HANA |
| File-based bulk transfer | SFTP + LSMW / BODS | Legacy; avoid for new designs |
| Real-time API (S/4HANA) | OData V4 via SAP API Business Hub | Check standard APIs first before custom |
| BTP integration | SAP Integration Suite (CPI) | For complex mappings; overkill for simple calls |
| Auth to SAP system | OAuth2 (S/4HANA) / Basic+SSL (ECC) | Never hardcode credentials |

## Critical SAP Objects by Domain

**Business Partner (S/4HANA mandatory)**
- Read: `/sap/opu/odata/sap/API_BUSINESS_PARTNER`
- Create: `BAPI_BUPA_CREATE_FROM_DATA`
- CVI prerequisite: Customer-Vendor-Integration must be active

**Material Master**
- Read: `BAPI_MATERIAL_GET_DETAIL`
- Create/Change: `BAPI_MATERIAL_SAVEDATA`
- S/4HANA: `API_PRODUCT_SRV` (OData)

**FI/GL**
- Posting: `BAPI_ACC_DOCUMENT_POST`
- Read GL: `BAPI_GL_GETGLACCPERIODVALUES`

**SD (Sales)**
- Sales Order: `BAPI_SALESORDER_CREATEFROMDAT2`
- Delivery: `BAPI_OUTB_DELIVERY_CONFIRM_DI`

**MM (Purchasing)**
- PO Create: `BAPI_PO_CREATE1`
- GR: `BAPI_GOODSMVT_CREATE` (mvt type 101)

**WM/EWM**
- EWM is separate system — use EWM OData APIs or PPF actions
- No direct BAPI for EWM warehouse orders — use EWM-specific function modules

## Common Pitfalls

1. **BAPI without COMMIT** — always call `BAPI_TRANSACTION_COMMIT` after write BAPIs
2. **RFC connection pooling** — PyRFC connections are expensive; pool them
3. **IDoc partner profiles** — must be configured before IDocs can flow; not automatic
4. **S/4HANA sandbox vs productive** — API availability differs; always check SAP API Business Hub
5. **Mandant isolation** — always parameterize the SAP client (Mandant) — never hardcode 100
6. **Change documents** — SAP logs all BAPI changes; plan for auditability
7. **Lock objects** — long-running reads don't lock; writes do; handle ENQUEUE errors

## BTP Architecture Decision Tree

```
Need SAP connectivity?
├── Simple API calls only → Direct RFC/OData from app (no BTP needed)
├── Complex transformation/mapping → SAP Integration Suite (CPI)
├── Multi-system orchestration → SAP Integration Suite + Event Mesh
├── User-facing app on SAP data → SAP Build Apps or custom on BTP CF
└── AI/ML on SAP data → BTP AI Core or external AI + OData read
```

## PyRFC Setup (Python backend connecting to SAP)

```python
from pyrfc import Connection

conn = Connection(
    ashost=SAP_HOST, sysnr=SAP_SYSNR,
    client=SAP_CLIENT, user=SAP_USER, passwd=SAP_PASS
)
result = conn.call('BAPI_MATERIAL_GET_DETAIL', MATERIAL='MAT001')
```

Requirements: `librfc` (SAP NW RFC Library) must be installed on the server.
On VPS Ubuntu: install via SAP download + `pip install pyrfc`.
