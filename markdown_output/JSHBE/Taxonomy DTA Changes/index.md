DTA

1.  Add subtype for source

2.  Send taskMap {content_id1: source_id1,content_id2: source_id1, cid3:
    src2} sending the tasks for a desk

3.  Remove the content_id from the assinged key when task is completed

4.  Save the source id in task table while marking completed

CMS

1.  Store qc_info array instead of flat data

2.  Make changes in Source ui to add filter for subtype

3.  Store the source_id,source_name with respect to each task completion
    in ES and activity log

QC Types

1.  Based on moderator

2.  Based on views -\> 500, 2500, 10k

3.  Internal\

jsontask_info -\> qc_info \[ { agency, type -\> views_qc_500,
completed_by, completed_time, status, source }, { agency, type -\>
internal, completed_by, completed_time, status, source }, { agency, type
-\> moderator, completed_by, completed_time, status, source } \]
