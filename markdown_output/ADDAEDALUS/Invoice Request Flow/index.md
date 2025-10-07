Before going to the invoice Request life cycle,Basic knowledge on
billing group creation and revenue locking is mandatory.Please make sure
you\'re familiar with the these concepts.

After locking revenue to a certain date you're allowed to create an
invoice request for a particular date range before locked revenue.

> possible status of invoice request

const STATUS_PENDING_APPROVAL_ON_SALES = 1; const
STATUS_REJECTED_BY_SALES = 2; const STATUS_PENDING_APPROVAL_ON_FINANCE =
3; const STATUS_REJECTED_BY_FINANCE = 4; const
STATUS_APPROVED_BY_FINANCE = 5; const
STATUS_INVOICE_CANCELLED_BY_FINANCE = 6; const
STATUS_RETRACTED_BY_FINANCE = 7; const STATUS_PENDING_APPROVAL_ON_CLIENT
= 8; const STATUS_REJECTED_BY_CLIENT = 9; const
STATUS_APPROVED_BY_CLIENT = 10; const STATUS_AUTO_APPROVED_BY_CLIENT =
11; const STATUS_INVOICE_GENERATED_AWAITING_COLLECTION = 12; const
STATUS_COLLECTED = 13; const STATUS_CREDIT_NOTE_SENT_TO_CLIENT = 14;
const STATUS_CANCELLED_BY_OPS =
15;4685e9e4-c078-4c6e-a45a-a1d9c67284a40468c8e7-c99e-4810-97d0-2acd35e53e41DECIDEDOnce
an invoice request is created,You're not allowed to create a new invoice
request unless in certain state(status).

- Once an invoice request is created,You're not allowed to create a new
  invoice request unless in certain state(status).

STATUS_PENDING_APPROVAL_ON_SALES

Once invoice request is created by AdOps it will be
STATUS_PENDING_APPROVAL_ON_SALES state and the future action will be
carried out by the sales team.form this status invoice request can be
moved to any one of the allowed status.

**Allowed status to change::**

STATUS_REJECTED_BY_SALES STATUS_PENDING_APPROVAL_ON_FINANCE
STATUS_CANCELLED_BY_OPS

`OPs team can cancle invoice request and moves to STATUS_CANCELLED_BY_OPS`
status.

STATUS_REJECTED_BY_SALES

Sales team can reject the request if any changes need to invoice
request.On this status AdOps team modifies any necessary data and
request again pushed to the first status
`STATUS_PENDING_APPROVAL_ON_SALES` for the approval.

**Allowed status to change::**

STATUS_PENDING_APPROVAL_ON_SALES STATUS_CANCELLED_BY_OPS

STATUS_PENDING_APPROVAL_ON_FINANCE

Once sales team Approves invoice request further action depends on
finance team.Next status can be either of fallowing status.

**Allowed status to change::**

STATUS_REJECTED_BY_FINANCE STATUS_APPROVED_BY_FINANCE
