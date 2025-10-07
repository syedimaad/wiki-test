#### Transactions Types

1.  Add Jems

    1.  Gift Sent

    2.  System Recieved

    3.  Purchase

2.  Reduce Jems

    1.  Gift Add

    2.  Reedemed

#### Wallet

1.  Create wallet → Once per user_id/client_id

2.  Update Wallet

    1.  Add Jems

        1.  Gift Sent

        2.  System Recieved

        3.  Purchase

    2.  Reduce Jems

        1.  Gift Add

        2.  Redeem Jems

#### APIs

1.  Transactions → Create/Update Transaction

2.  Wallet → Create/Update Wallet

#### Controller

1.  Transactions

    1.  Create Request

    2.  Update Request

    3.  GetTransactionsList

2.  Wallet

    1.  GetJemsBalance

#### Service

1.  Transaction

    1.  Create/Update Transaction

        1.  Type

        2.  Status -\> begin/in_progress/success/failure

        3.  Extra Param -\> rpay_trans_id, text, milestone_id,
            activity_id, amount

2.  Wallet

    1.  GetJemsBalance -\> wallet_id

    2.  Update Wallet -\> Type, Operation, Amount

    3.  Create wallet for new user -\> user_id/client_id, type, amount

#### Builder

1.  Transaction

2.  Wallet

#### Status Mapping

  -------------------- ------------------------ --------------------- --------------------------------------------------------------------------------------------------
  **Request Status**   **Transaction Status**   **RazorPay Status**   **Comments**
  BEGIN                STARTED                                        Scheduler to check started ones and move to TERMINATED after 24 hours
  UPDATE               IN_PROGRESS              CREATED               On request from PWA
  END                  FAILED                   FAILED                On request from PWA
  END                  SUCCESS                  CAPTURED              On request from PWA → Check with Razor Pay on the transaction status → if CAPTURED → Credit Jems
  END                  IN_PROGRESS              AUTHORISED            On request from PWA
                       IN_PROGRESS                                    Keep checking against razor pay for status till 5 days from transaction_start_time
                       FAILED                   REFUNDED              Once the in_progress ones have moved to refunded from razor pay
  -------------------- ------------------------ --------------------- --------------------------------------------------------------------------------------------------
