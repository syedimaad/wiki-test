## Tables Effected

[N.B: Below changes are applicable for alphanumeric
only.]{style="color: rgb(191,38,0);"}

  ------------------------------------------------ ------------------------------------------------- ---------------------------------------------------------- ------------------------------------------------------- ------------------------------------------------- -------------------------------------------------------------
  [Main Table]{style="color: rgb(255,255,255);"}   [Primary Key]{style="color: rgb(255,255,255);"}   [Associated Databases]{style="color: rgb(255,255,255);"}   [Associated Tables]{style="color: rgb(255,255,255);"}   [Foreign Key]{style="color: rgb(255,255,255);"}   [Column Data type change]{style="color: rgb(255,255,255);"}
  dhx_orders                                       id                                                daedalus                                                   dhx_client_report_mail_scheduler                        order_id                                          Int → Varchar(50)
                                                                                                     daedalus                                                   dhx_invoice_requests                                    order_id                                          Int → Varchar(50)
                                                                                                     daedalus                                                   dhx_mail_scheduler                                      order_id                                          Int → Varchar(50)
                                                                                                     daedalus                                                   dhx_orders_history                                      order_id                                          Int → Varchar(50)
                                                                                                     daedalus                                                   dhx_orders_history_for_downloads                        order_id                                          Int → Varchar(50)
                                                                                                     daedalus                                                   dhx_report_groups                                       order_id                                          Int → Varchar(50)
                                                                                                     daedalus                                                   dhx_requirements                                        order_id                                          Int → Varchar(50)
                                                                                                     daedalus                                                   dhx_requirements_groups                                 order_id                                          Int → Varchar(50)
                                                                                                     daedalus                                                   dhx_requirements_history                                order_id                                          Int → Varchar(50)
                                                                                                     daedalus                                                   dhx_third_party_custom_reports                          order_id                                          Int → Varchar(50)
                                                                                                     daedalus                                                   users                                                   default_order_id                                  Int → Varchar(50)
  ------------------------------------------------ ------------------------------------------------- ---------------------------------------------------------- ------------------------------------------------------- ------------------------------------------------- -------------------------------------------------------------

## **Steps**

**Pre-steps:**

1.  Learning model update - with fallbacks

**During:**

1.  Backup

2.  DD turns off

3.  MPE turn off - Maintenance and state changes

4.  SQL changes

5.  Code changes

    1.  Ranking

    2.  Data pipeline

    3.  Daedalus

    4.  adEngine

6.  MPE start

7.  DD start

## Queries To Run

  ---------------------------------------------- ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- ----------------------------------------------
  [Database]{style="color: rgb(255,255,255);"}   [Query]{style="color: rgb(255,255,255);"}                                                                                                                              [Comments]{style="color: rgb(255,255,255);"}
  daedalus                                       ALTER TABLE \`dhx_orders\` CHANGE \`id\` \`id\` VARCHAR(50) NOT NULL;                                                                                                  **Don't Trigger**
  daedalus                                       ALTER TABLE \`dhx_orders\` ADD \`id_temp\` INT NOT NULL AUTO_INCREMENT, ADD INDEX (\`id_temp\`);                                                                       **Don't Trigger**
  daedalus                                       UPDATE \`dhx_orders\` SET \`id_temp\`=\`id\`;                                                                                                                          **Don't Trigger**
  daedalus                                       ALTER TABLE \`dhx_client_report_mail_scheduler\` CHANGE \`order_id\` \`order_id\` VARCHAR(50) NOT NULL;                                                                **Don't Trigger**
  daedalus                                       ALTER TABLE \`dhx_invoice_requests\` CHANGE \`order_id\` \`order_id\` VARCHAR(50) NOT NULL;                                                                            **Don't Trigger**
  daedalus                                       ALTER TABLE \`dhx_mail_scheduler\` CHANGE \`order_id\` \`order_id\` VARCHAR(50) NOT NULL;                                                                              **Don't Trigger**
  daedalus                                       ALTER TABLE \`dhx_orders_history\` CHANGE \`order_id\` \`order_id\` VARCHAR(50) NOT NULL;                                                                              **Don't Trigger**
  daedalus                                       ALTER TABLE \`dhx_orders_history_for_downloads\` CHANGE \`order_id\` \`order_id\` VARCHAR(50) CHARACTER SET latin1 COLLATE latin1_swedish_ci NOT NULL DEFAULT \'0\';   **Don't Trigger**
  daedalus                                       ALTER TABLE \`dhx_report_groups\` CHANGE \`order_id\` \`order_id\` VARCHAR(50) NOT NULL;                                                                               **Don't Trigger**
  daedalus                                       ALTER TABLE \`dhx_requirements\` CHANGE \`order_id\` \`order_id\` VARCHAR(50) NOT NULL;                                                                                **Don't Trigger**
  daedalus                                       ALTER TABLE \`dhx_requirements_groups\` CHANGE \`order_id\` \`order_id\` VARCHAR(50) NOT NULL;                                                                         **Don't Trigger**
  daedalus                                       ALTER TABLE \`dhx_requirements_history\` CHANGE \`order_id\` \`order_id\` VARCHAR(50) NOT NULL;                                                                        **Don't Trigger**
  daedalus                                       ALTER TABLE \`dhx_third_party_custom_reports\` CHANGE \`order_id\` \`order_id\` VARCHAR(50) CHARACTER SET latin1 COLLATE latin1_swedish_ci NOT NULL;                   **Don't Trigger**
  daedalus                                       ALTER TABLE \`users\` CHANGE \`default_order_id\` \`default_order_id\` VARCHAR(50) CHARACTER SET latin1 COLLATE latin1_swedish_ci NULL DEFAULT NULL;                   **Don't Trigger**
  daedalus                                       ALTER TABLE \`dhx_client_report_mail_scheduler\` ADD FOREIGN KEY (\`order_id\`) REFERENCES \`dhx_orders\`(\`id\`) ON DELETE RESTRICT ON UPDATE CASCADE;                
  daedalus                                       ALTER TABLE \`dhx_invoice_requests\` ADD FOREIGN KEY (\`order_id\`) REFERENCES \`dhx_orders\`(\`id\`) ON DELETE RESTRICT ON UPDATE CASCADE;                            
  daedalus                                       ALTER TABLE \`dhx_mail_scheduler\` ADD FOREIGN KEY (\`order_id\`) REFERENCES \`dhx_orders\`(\`id\`) ON DELETE RESTRICT ON UPDATE CASCADE;                              
  daedalus                                       ALTER TABLE \`dhx_orders_history\` ADD FOREIGN KEY (\`order_id\`) REFERENCES \`dhx_orders\`(\`id\`) ON DELETE RESTRICT ON UPDATE CASCADE;                              
  daedalus                                       ALTER TABLE \`dhx_orders_history_for_downloads\` ADD FOREIGN KEY (\`order_id\`) REFERENCES \`dhx_orders\`(\`id\`) ON DELETE RESTRICT ON UPDATE CASCADE;                
  daedalus                                       ALTER TABLE \`dhx_report_groups\` ADD FOREIGN KEY (\`order_id\`) REFERENCES \`dhx_orders\`(\`id\`) ON DELETE RESTRICT ON UPDATE CASCADE;                               
  daedalus                                       ALTER TABLE \`dhx_requirements\` ADD FOREIGN KEY (\`order_id\`) REFERENCES \`dhx_orders\`(\`id\`) ON DELETE RESTRICT ON UPDATE CASCADE;                                
  daedalus                                       ALTER TABLE \`dhx_requirements_groups\` ADD FOREIGN KEY (\`order_id\`) REFERENCES \`dhx_orders\`(\`id\`) ON DELETE RESTRICT ON UPDATE CASCADE;                         
  daedalus                                       ALTER TABLE \`dhx_requirements_history\` ADD FOREIGN KEY (\`order_id\`) REFERENCES \`dhx_orders\`(\`id\`) ON DELETE RESTRICT ON UPDATE CASCADE;                        
  daedalus                                       ALTER TABLE \`dhx_third_party_custom_reports\` ADD FOREIGN KEY (\`order_id\`) REFERENCES \`dhx_orders\`(\`id\`) ON DELETE RESTRICT ON UPDATE CASCADE;                  
  daedalus                                       UPDATE \`dhx_orders\` SET id = uuid() WHERE id \> 0;                                                                                                                   **Don't Trigger**
  daedalus                                       UPDATE users a INNER JOIN dhx_orders b ON a.default_order_id = b.id_temp SET a.default_order_id = [b.id](http://b.id);                                                 **Don't Trigger**
  ---------------------------------------------- ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- ----------------------------------------------

## Deployment Status

  ------------------------------------------------- ------------------------------------------------- ---------------------------------------------
  [Environment]{style="color: rgb(255,255,255);"}   [Avalability]{style="color: rgb(255,255,255);"}   [Testing]{style="color: rgb(255,255,255);"}
  GCP QA                                            No                                                
  GCP PRE-PROD                                      Yes                                               
  GCP PROD                                                                                            
  ------------------------------------------------- ------------------------------------------------- ---------------------------------------------

## Issues Occured & Resolution that was done

  --------------------------------------------------- ------------------------------------------------
  [Issue Occured]{style="color: rgb(255,255,255);"}   [Resolution]{style="color: rgb(255,255,255);"}
                                                      
                                                      
                                                      
                                                      
                                                      
                                                      
  --------------------------------------------------- ------------------------------------------------
