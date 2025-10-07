**Flow and Relations**

`dhx_context_meta` tables contains contextTag (pub and hubs) rules which
are be decoded by the Client In order to evaluate for further decision
making.

tables:

`dhx_content_contexts`

`dhx_context_meta`

`dhx_content_context_history`

`dhx_hubs`

`dhx_publishers`

`dhx_content_contexts` table is used to keep rules for hubs and
pubs(hubs and pubs can be picked from master tables `dhx_hubs` and
`dhx_publishers`)

each time a entry added to `dhx_content_contexts` than a method
(`ContextMeta::updateEntityContextMeta`) will update `dhx_context_meta`
table by fetching all the rules from `dhx_content_contexts` for that
hostApp(DH_MENA and DH_APP)

Note: `dhx_context_meta` contains all data formatted from
`dhx_content_contexts` for each hostApp.

`dhx_content_context_history` will keep the history of
`dhx_content_contexts` tables updates , creates and deletes

Any update to `dhx_content_context_history` and `dhx_hubs` will lead an
update in `dhx_context_meta`.

Note :: Need more clarity of these rules from others teams .
