Invoice Classified as three types which are Associated with Order.

const TYPE_PREPAID = 0; const TYPE_POSTPAID = 1; const TYPE_DIRECT = 2;

Each Invoice can have either of 3 status

const STATUS_NEW = 0; const STATUS_READY = 1; const STATUS_FAILED = 2;

Whenever an Invoice created, the default status would be `STATUS_NEW`.

At certain point of time Invoice Pdf going to be generated along with
html,On Success of pdf generation status will be updated to
`STATUS_READY` other wise `STATUS_FAILED` and the failed reason & html
maintained in invoice table.

Invoice Classification directly related to Orders, While there is no
direct relation Maintained in database.

Invoice Creation Source & related tables can be varies based
Classification of Invoices.

`TYPE_PREPAID` Invoices can be created along with mojo transaction.

Route::post(\'api/payment/mojo-payment-hook\', \[\"uses\" =\>
\"PaymentGatewayController@mojoPaymentHook\"\]);

A Cron Job is scheduled to Generated `TYPE_POSTPAID` invoice every month
with specify details like user_id , year and months.

MonthlyInvoiceGenerator.php

Before creating `TYPE_DIRECT` invoice ,An `InvoiceRequests` has to be
approved by sales and finance on invoicing details and the these
`InvoiceRequests` status will be maintained in `dhx_invoice_requests`
table.
