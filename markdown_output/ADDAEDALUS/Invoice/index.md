## Tables Effected

  ------------------------------------------------ ------------------------------------------------- ---------------------------------------------------------- ------------------------------------------------------- ------------------------------------------------- -------------------------------------------------------------
  [Main Table]{style="color: rgb(255,255,255);"}   [Primary Key]{style="color: rgb(255,255,255);"}   [Associated Databases]{style="color: rgb(255,255,255);"}   [Associated Tables]{style="color: rgb(255,255,255);"}   [Foreign Key]{style="color: rgb(255,255,255);"}   [Column Data type change]{style="color: rgb(255,255,255);"}
  dhx_invoice                                      id                                                daedalus                                                   dhx_credit_notes                                        invoice_id                                        Int → Varchar(50)
                                                                                                     daedalus                                                   dhx_invoice_collections                                 invoice_id                                        Int → Varchar(50)
                                                                                                     daedalus                                                   dhx_invoice_credits                                     invoice_id                                        Int → Varchar(50)
  ------------------------------------------------ ------------------------------------------------- ---------------------------------------------------------- ------------------------------------------------------- ------------------------------------------------- -------------------------------------------------------------

## Queries To Run

  ---------------------------------------------- --------------------------------------------------------------------------------------------------------------------------------------------------- ----------------------------------------------
  [Database]{style="color: rgb(255,255,255);"}   [Query]{style="color: rgb(255,255,255);"}                                                                                                           [Comments]{style="color: rgb(255,255,255);"}
  daedalus                                       ALTER TABLE \`dhx_invoice\` CHANGE \`id\` \`id\` VARCHAR(50) NOT NULL;                                                                              
  daedalus                                       ALTER TABLE \`dhx_invoice\` ADD \`id_temp\` INT NOT NULL AUTO_INCREMENT, ADD INDEX (\`id_temp\`);                                                   
  daedalus                                       UPDATE \`dhx_invoice\` SET \`id_temp\`=\`id\`;                                                                                                      
  daedalus                                       ALTER TABLE \`dhx_credit_notes\` CHANGE \`invoice_id\` \`invoice_id\` VARCHAR(50) NOT NULL;                                                         
  daedalus                                       ALTER TABLE \`dhx_invoice_collections\` CHANGE \`invoice_id\` \`invoice_id\` VARCHAR(50) NOT NULL;                                                  
  daedalus                                       ALTER TABLE \`dhx_invoice_credits\` CHANGE \`invoice_id\` \`invoice_id\` VARCHAR(50) NOT NULL;                                                      
  daedalus                                       ALTER TABLE \`dhx_credit_notes\` ADD FOREIGN KEY (\`invoice_id\`) REFERENCES \`dhx_invoice\`(\`id\`) ON DELETE RESTRICT ON UPDATE CASCADE;          
  daedalus                                       ALTER TABLE \`dhx_invoice_collections\` ADD FOREIGN KEY (\`invoice_id\`) REFERENCES \`dhx_invoice\`(\`id\`) ON DELETE RESTRICT ON UPDATE CASCADE;   
  daedalus                                       ALTER TABLE \`dhx_invoice_credits\` ADD FOREIGN KEY (\`invoice_id\`) REFERENCES \`dhx_invoice\`(\`id\`) ON DELETE RESTRICT ON UPDATE CASCADE;       
  daedalus                                       UPDATE \`dhx_invoice\` SET \`id\`= uuid()                                                                                                           **Don't Trigger**
  ---------------------------------------------- --------------------------------------------------------------------------------------------------------------------------------------------------- ----------------------------------------------

## Deployment Status

  ------------------------------------------------- ------------------------------------------------- ---------------------------------------------
  [Environment]{style="color: rgb(255,255,255);"}   [Avalability]{style="color: rgb(255,255,255);"}   [Testing]{style="color: rgb(255,255,255);"}
  GCP QA                                            Yes                                               Done
  GCP PRE-PROD                                      Yes                                               Done
  GCP PROD                                          Waiting for approval                              
  ------------------------------------------------- ------------------------------------------------- ---------------------------------------------

## Issues Occured & Resolution That Was Done

  --------------------------------------------------- ------------------------------------------------
  [Issue Occured]{style="color: rgb(255,255,255);"}   [Resolution]{style="color: rgb(255,255,255);"}
                                                      
                                                      
                                                      
                                                      
                                                      
                                                      
  --------------------------------------------------- ------------------------------------------------
