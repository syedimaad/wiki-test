## Tables Effected

  ------------------------------------------------ ------------------------------------------------- ---------------------------------------------------------- ------------------------------------------------------- ------------------------------------------------- -------------------------------------------------------------
  [Main Table]{style="color: rgb(255,255,255);"}   [Primary Key]{style="color: rgb(255,255,255);"}   [Associated Databases]{style="color: rgb(255,255,255);"}   [Associated Tables]{style="color: rgb(255,255,255);"}   [Foreign Key]{style="color: rgb(255,255,255);"}   [Column Data type change]{style="color: rgb(255,255,255);"}
  dhx_sales_leads                                  id                                                daedalus                                                   dhx_sales_lead_log                                      lead_id                                           Int → Varchar(50)
                                                                                                     daedalus                                                   dhx_sales_csm_support_request                           lead_id                                           Int → Varchar(50)
                                                                                                     daedalus                                                   dhx_sales_proposals                                     lead_id                                           Int → Varchar(50)
                                                                                                     daedalus                                                   dhx_orders                                              lead_id                                           Int → Varchar(50)
                                                                                                     daedalus                                                   dhx_upload                                              link_id                                           Int → Varchar(50)
                                                                                                     daedalus                                                   dhx_approve_reject_requests                             entity_id                                         Int → Varchar(50)
  ------------------------------------------------ ------------------------------------------------- ---------------------------------------------------------- ------------------------------------------------------- ------------------------------------------------- -------------------------------------------------------------

## Queries To Run

  ---------------------------------------------- ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ ----------------------------------------------
  [Database]{style="color: rgb(255,255,255);"}   [Query]{style="color: rgb(255,255,255);"}                                                                                                                                                        [Comments]{style="color: rgb(255,255,255);"}
  daedalus                                       ALTER TABLE \`dhx_sales_leads\` CHANGE \`id\` \`id\` VARCHAR(50) NOT NULL;                                                                                                                       
  daedalus                                       ALTER TABLE \`dhx_sales_leads\` ADD \`id_temp\` INT NOT NULL AUTO_INCREMENT, ADD INDEX (\`id_temp\`);                                                                                            
  daedalus                                       UPDATE \`dhx_sales_leads\` SET \`id_temp\`=\`id\`                                                                                                                                                
  daedalus                                       ALTER TABLE \`dhx_sales_lead_log\` CHANGE \`lead_id\` \`lead_id\` VARCHAR(50) NOT NULL;                                                                                                          
  daedalus                                       ALTER TABLE \`dhx_sales_proposals\` CHANGE \`lead_id\` \`lead_id\` VARCHAR(50) NOT NULL;                                                                                                         
  daedalus                                       ALTER TABLE \`dhx_sales_csm_support_request\` CHANGE \`lead_id\` \`lead_id\` VARCHAR(50) NOT NULL;                                                                                               
  daedalus                                       ALTER TABLE \`dhx_orders\` CHANGE \`lead_id\` \`lead_id\` VARCHAR(50) NULL DEFAULT NULL;                                                                                                         
  daedalus                                       ALTER TABLE \`dhx_upload\` CHANGE \`link_id\` \`link_id\` VARCHAR(50) NOT NULL;                                                                                                                  
  daedalus                                       ALTER TABLE \`dhx_approve_reject_requests\` CHANGE \`entity_id\` \`entity_id\` VARCHAR(50) NOT NULL;                                                                                             
  daedalus                                       ALTER TABLE \`dhx_sales_lead_log\` ADD FOREIGN KEY (\`lead_id\`) REFERENCES \`dhx_sales_leads\`(\`id\`) ON DELETE RESTRICT ON UPDATE CASCADE;                                                    
  daedalus                                       ALTER TABLE \`dhx_sales_proposals\` ADD FOREIGN KEY (\`lead_id\`) REFERENCES \`dhx_sales_leads\`(\`id\`) ON DELETE RESTRICT ON UPDATE CASCADE;                                                   
  daedalus                                       ALTER TABLE \`dhx_sales_csm_support_request\` ADD FOREIGN KEY (\`lead_id\`) REFERENCES \`dhx_sales_leads\`(\`id\`) ON DELETE RESTRICT ON UPDATE CASCADE;                                         
  daedalus                                       ALTER TABLE \`dhx_orders\` ADD FOREIGN KEY (\`lead_id\`) REFERENCES \`dhx_sales_leads\`(\`id\`) ON DELETE RESTRICT ON UPDATE CASCADE;                                                            
  daedalus                                       UPDATE \`dhx_sales_leads\` SET \`id\`= uuid();                                                                                                                                                   **Don't Trigger**
  daedalus                                       UPDATE dhx_upload a LEFT JOIN dhx_sales_leads b ON a.link_id = b.id_temp SET a.link_id = [http://b.id](http://b.id){card-appearance="inline"} WHERE a.entity_type = \"salesLeads\";              **Don't Trigger**
  daedalus                                       UPDATE dhx_approve_reject_requests a LEFT JOIN dhx_sales_leads b ON a.entity_id = b.id_temp SET a.entity_id = [http://b.id](http://b.id){card-appearance="inline"} WHERE a.entity_type_id = 3;   **Don't Trigger**
  ---------------------------------------------- ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ ----------------------------------------------

## Deployment Status

  ------------------------------------------------- ------------------------------------------------ ---------------------------------------------
  [Environment]{style="color: rgb(255,255,255);"}   [Deployment]{style="color: rgb(255,255,255);"}   [Testing]{style="color: rgb(255,255,255);"}
  GCP QA                                            Done                                             Done
  GCP PRE-PROD                                      Done                                             Done
  GCP PROD                                          Done                                             Done
  ------------------------------------------------- ------------------------------------------------ ---------------------------------------------

## Issues Occurred & Resolution that Was Done

  --------------------------------------------------- ------------------------------------------------
  [Issue Occured]{style="color: rgb(255,255,255);"}   [Resolution]{style="color: rgb(255,255,255);"}
                                                      
                                                      
                                                      
                                                      
                                                      
                                                      
  --------------------------------------------------- ------------------------------------------------
