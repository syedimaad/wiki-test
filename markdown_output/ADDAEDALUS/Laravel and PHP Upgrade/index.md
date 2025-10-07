Aim to Upgrade PHP7.1 to PHP8.0

Needed laravel version is 6.x for PHP8 Current version is 5.2.

Approche

Laravel Docs provides step by step flow to upgrade the framework

5.2 to 5.3 to 5.4 to 5.5 to 5.6 to 5.8 to 6.x

PHP also has the doc to Upgrade php versions

7.1 to 7.2 to 7.3 to 7.4 to 8.0

Composer.phar has been to upgraded to 2.5.4 for php8 support

These steps should be flowed to minimise the bugs and not leaving any
unidentified errors in the system.As well one must read each upgrade doc
so that future errors can be traced done and possible to fix.

Prod Deployment Status

> **Installation Status** : Installed all the Extensions in Prod 97
> Vm.Tested All the view pages to verify. All routes are working
>
> LibZip \>1.0.0 has been installed and tested.
>
> SelfServe routes are working. Campaign and banner creation not tested.
>
> Tested CR1 Reports
>
> Tested Revenue monitor section for 1 month data.
>
> DH and Josh campaign , banner creation . DH activation tested in Order
> Id 1.
>
> Banner bulk upload has been tested(for zip test).
>
> Inventory Estimation test for all HostAppIds.(including audience reach
> ones)
>
> Tested Exchange Rate Api.

## Post Deployment Testing Section

1.Google login

**Files changed and Third party package changes**

!Changes included for Upgrade \* admis_php/app/Console/Kernel.php method
added to autoload all the commands(no need to include specifically) \*
admis_php/app/Exceptions/Handler.php unauthenticated method added as per
the laravel upgrade \*
admis_php/app/Http/Controllers/API/SpeedScoreController.php \*
admis_php/app/Modules/PageSpeed.php PhpInsights lib packages does\'t
support php8 \* admis_php/app/Http/Controllers/AdvertiserController.php
\* admis_php/app/Http/Controllers/Daedalus/CouponController.php \*
admis_php/app/Http/Controllers/Daedalus/S2STagsController.php \*
admis_php/app/Http/Controllers/HealthCheckController.php \*
admis_php/app/Http/Controllers/ReportsController.php (also show method
removed no use at all , link(getExecutor method)) \*
admis_php/app/Http/Controllers/SettingsController.php \*
admis_php/app/Http/Controllers/SpoofController.php \*
admis_php/app/Http/Controllers/TagsController.php \*
admis_php/app/Http/Controllers/UserController.php (also elequent lists
method deprectaed in one of laravel versions (5.4 i guess)) \*
admis_php/app/Http/Controllers/cpc_Controller.php (also removed
Illuminate\\Http\\Request(no use) , input::get changes to Request::input
(as per the doc, can use get too)) \*
admis_php/app/Http/Controllers/loginController.php (Input:get replaced
with the Request::input) \*
admis_php/app/Http/Controllers/reportController.php (also removed
Illuminate\\Http\\Request(no use) ) \*
admis_php/app/Http/Controllers/socialController.php (lso removed
Illuminate\\Http\\Request(no use)) \*
admis_php/app/Http/Controllers/viewController.php (also removed
Illuminate\\Http\\Request(no use)) Illuminate\\Support\\Facades\\Input
has been removed ,its is replica of Request Facades (look in app.php) \*
admis_php/app/Http/Controllers/AudienceSegmentController.php \*
admis_php/app/Http/Controllers/LeadsController.php FileExport removed \*
admis_php/app/Http/Controllers/Auth/AuthController.php \*
admis_php/app/Http/Controllers/Auth/PasswordController.php delted as per
laravel upgrade document \*
admis_php/app/Http/Controllers/Auth/ForgotPasswordController.php \*
admis_php/app/Http/Controllers/Auth/LoginController.php \*
admis_php/app/Http/Controllers/Auth/RegisterController.php \*
admis_php/app/Http/Controllers/Auth/ResetPasswordController.php file
included as per laravel upgrade document \*
admis_php/app/Http/Controllers/ClientReportsController.php \*
admis_php/app/Http/Controllers/Daedalus/Banners/VastVideoBannerController.php
\* admis_php/app/Http/Controllers/WalletSelfCreditController.php \*
admis_php/app/Models/Daedalus/BannerFeatures.php (created an moduel for
the support, FormatIdentifier) Excel Removed from the include files
(Maatwebsite\\Excel\\Facades\\Excel is deprecated in laravel 5.8) \*
admis_php/app/Http/Controllers/Controller.php AuthorizesResources trait
added as per laravel upgrade documents \*
admis_php/app/Http/Controllers/TestController.php never mind \*
admis_php/app/Http/Kernel.php value of \'can\' key been replaced with
\\Illuminate\\Auth\\Middleware\\Authorize::class as per the laravel
upgrade doc and \'bindings\' key added to \'api\' \*
admis_php/app/Http/Middleware/authCheck.php
\$request-\>route()-\>getPath(); replaced with \$route =
\$request-\>route()-\>uri(); (getPath methos has been removed in
Illuminate\\Http\\Request as per the laravel doc ) \*
admis_php/app/Http/routes.php \*
admis_php/app/Providers/AppServiceProvider.php forceSchema mrthod from
\\URL has renamed to forceScheme (not use php upgrade or laravel (mostly
laravel it seems)) \* admis_php/app/Models/AppEventReports.php \*
admis_php/app/Models/DailyRevenueReportCache.php \*
admis_php/app/Models/LanguageReport.php \*
admis_php/app/Models/LinQ/PerformanceReportsSource.php \*
admis_php/app/Models/LocationReports.php \*
admis_php/app/Models/NetworkSpeedReports.php \*
admis_php/app/Models/PerformanceReports.php \*
admis_php/app/Models/PhoneBrandReport.php \*
admis_php/app/Models/PhonePriceReport.php \*
admis_php/app/Models/PlacementReport.php \*
admis_php/app/Models/ReachReport.php \* admis_php/app/Models/Reports.php
(also getExecutor method removed since ReportsExecutor is removed fron
dd) \* admis_php/app/Models/TODPerformanceReports.php \*
admis_php/app/Models/ZonePerformanceReports.php
App\\Modules\\ReportsExecutor removed from included files (no use) \*
admis_php/app/Models/CRM/SalesLeads.php \*
admis_php/app/Models/Invoice/Invoice.php as of laravel 6 , models needs
to define the protected \$keyType = \'string\'; if the primarykey type
is string (has to do with tight coupling some sort , not sure) \*
admis_php/app/Models/DFP/LineItems.php array_key_exists does\'t works
with objects as per laravel upgrade doc(works in laravel 5.2), so
replced with \* admis_php/app/Models/Events/EventPostback.php static
propertu \$events has been renamed to \$eventTypes (laravel internally
uses \$events, as per doc) \* admis_php/app/Models/Orders.php count
function removed on \$invoiceRequest-\>invoice in 4 places ,since from
now on laravel will always returns the collection not the array both for
eloquant and query builder(calling -\>all on colection will convert to
array) \* admis_php/app/Modules/AggressiveCacher.php \*
admis_php/app/Modules/ImageDeployer.php \*
admis_php/app/Modules/RemoteVideoConverter.php (not using ssh) \*
admis_php/app/Modules/ReportFetchPostProcess.php (not using ssh) SSH
removed laravelremotecollection has deprecated , (will find new approche
to run the AggressiveCacher, moslty api ) \*
admis_php/app/Modules/FileExport.php file removed , since using Excel
(deprecated) \* admis_php/app/Modules/FormatIdentifier.php
admis_php/vendor/maatwebsite/excel/src/Maatwebsite/Excel/Classes/FormatIdentifier.php
has been removed and same code included in the file. \*
admis_php/app/Modules/ImageProcessor.php ImageBuilder has been removed ,
deprecated \* admis_php/app/Modules/MailEntityHandler.php \*
admis_php/app/Modules/MailEntityHandlerV2.php method
(dateSortDescCompFunction) .php8 , sort function will not take true or
false in the callback fucntuon will take 0 , greate than and less than
zero (like spaceoperter \<=\>) \*
admis_php/app/Modules/ReportsExecutor.php file deleted not used \*
admis_php/app/Modules/ZipReader.php zip_open , zip_read etc are
deprecated in php8 so using ZipArchive(tested to working) \*
admis_php/app/Providers/AuthServiceProvider.php \*
admis_php/app/Providers/EventServiceProvider.php \*
admis_php/app/Providers/RouteServiceProvider.php \*
admis_php/config/mail.php changes done as per laravel upgrade doc \*
admis_php/app/Providers/BroadcastServiceProvider.php file included as
per laravel upgrade doc \* admis_php/composer.json \*
admis_php/composer.lock packges \* admis_php/composer.phar 2.5.4 version
added (1.2.2 does\'t support higher php versions) \*
admis_php/config/app.php SSH and Excel removed from aliases array (they
are not available on higher laravel and php versions)
Maatwebsite\\Excel\\ExcelServiceProvider::class and
Collective\\Remote\\RemoteServiceProvider::class they are not available
on higher laravel and php versions) added some service porivders which
are available in current laravel version \* admis_php/config/hashing.php
\* admis_php/config/logging.php added as per laravel doc.(included just
incase of use) , new laravel feathers \* admis_php/config/queue.php
expire key renamed to retry_after as per doc \*
admis_php/public/svg/403.svg \* admis_php/public/svg/404.svg \*
admis_php/public/svg/500.svg \* admis_php/public/svg/503.svg added as
per laravel upgrade doc. good svgs can be usable \*
admis_php/resources/views/daedalus/upload-filejs.blade.php or has been
removed in favor of ?? (not use its a laravel balde or general php
changes) \* admis_php/storage/framework/cache/.gitignore added as per
laravel upgrade doc data folder in admis_php/storage/framework/cache
should be added as per doc (not sure why) \*\*\* vendor folder changes
packages removed \"maatwebsite/excel\": \"\^2.1\",
\"laravelcollective/remote\": \"5.2\", \"symfony/translation\":
\"2.8.9\", \"coldume/imagecraft\": \"\^1.0\", \"dsentker/phpinsights\":
\"\^0.2.1\", packages Added \"laravel/tinker\": \"\^1.0\",
\"laravel/helpers\": \"\^1.6\" (array_get and pluck methods, they are
deprecated in laravel 6 so new package) \"filp/whoops\":\"\~2.0\"
packages Upgraded \"laravel/framework\": \"\^6.0\", from
\"laravel/framework\": \"5.2.\*\", \"symfony/event-dispatcher\":
\"\~4.0\", from \"symfony/event-dispatcher\": \"2.8.9\",
\"phpunit/phpunit\": \"\~9.0\", from \"phpunit/phpunit\": \"\~4.0\",
\"symfony/css-selector\": \"2.8.\*\|3.0.\*\" from
\"symfony/css-selector\": \"3.1.\*\", \"symfony/dom-crawler\":
\"2.8.\*\|3.0.\*\" from \"symfony/dom-crawler\": \"3.1.\*\", \"php
artisan optimize\" deprecated Must Run Commands after deployment php
artisan cache:clear php artisan config:clear php artisan view:clear php
artisan route:clear

Git Branches. Actively maintaining
**DD-master-27-feb-23-laravel-6.20.44-php@8.0.28-composer-2.5.4** branch
only.

 DD-master-17-feb-23-laravel-5.3.31

  DD-master-17-feb-23-laravel-5.4.36

  DD-master-20-feb-23-laravel-5.4.36-php@7.4.33-composer-2.5.4

  DD-master-23-feb-23-laravel-5.5.50-php@7.4.33-composer-2.5.4

  DD-master-23-feb-23-laravel-5.6.40-php@7.4.33-composer-2.5.4

  DD-master-23-feb-23-laravel-5.7.29-php@7.4.33-composer-2.5.4

  DD-master-23-feb-23-laravel-5.8.38-php@7.4.33-composer-2.5.4

  DD-master-27-feb-23-laravel-6.20.44-php@7.4.33-composer-2.5.4

DD-master-27-feb-23-laravel-6.20.44-php@8.0.28-composer-2.5.4

> Latest Branch has been pushed to sandbox

**Pending tasks**

SSH Dependency Removed and API Call for Aggressive cache needs to be
tested.

**Current Prod PHP7.1 Extensions**

appdynamics_agent bcmath bz2 calendar Core ctype curl date dom exif
fileinfo filter ftp gd gettext grpc hash hll iconv imagick imap json
libxml mbstring mcrypt mongodb mysqli mysqlnd openssl pcntl pcre PDO
pdo_mysql pdo_pgsql pdo_sqlite pgsql Phar posix protobuf Reflection
session SimpleXML soap sockets SPL sqlite3 standard sysvsem sysvshm tidy
tokenizer xml xmlreader xmlrpc xmlwriter xsl zip zlib

**some main PHP Extensions to emphasise on**

grpc imagick hll mongodb Zip with lizip Version \> 1.0.0 (must be tested
in any case)

**Testing needed modules**

1.Leads to order creation flow.

2.Order to banner creation flow.(including activation of campaign and
banners)

3.Billing Group and Requirement Group Creation

4.locking the order along with the invoice generation flow(adops, sales
and finance dashboards)

5.Revenue Monitor section (Revenue reports with some filters)

[6.CR](http://6.CR) Daily Mails and checking the numbers.

7.Adengine Apis should be tested.(Aggressive is one of them)

8.Block PostIds section for both DH_APP and DH_MENA.

9.Self Serve Section

Install HLL

Prerequisite :

1.find php-config for php8.0 and php.ini

Steps

1.Clone phphll

2.Remove \'phpize\' in Makefile line number 34 under php: libhll.a
section

3.Replace all content in hll.c with the update bug free code for php8.0

4.run command cd php && phpize

5.open php/configure replace php-config with php8.0 php-config
path(absolute path) in line 4190 php_with_php_config 4200 PHP_PHP_CONFIG

6.run make php(in phphll directory , check for errors)

7.run cd php && sudo make install

8.add extension=hll.so in php.ini file

Extra Info Stage php8.0 config file path and .ini file

/mnt/vol1/dh-ads/php-8.0.28/bin/php-config

/mnt/vol1/dh-ads/php-8.0.28/lib/php.ini

#include \"php_hll.h\" #include \"../hyperloglog.h\" #include
\<zend_exceptions.h\> #include \<zend_types.h\> #include
\<ext/standard/php_var.h\> #define zend_uint uint32_t /\* {{{ macros \*/
#define HLL_ARG_ONLY()\\ robj \*hll;\\ zval \*hll_resource;\\ if
(zend_parse_parameters(ZEND_NUM_ARGS(), \"r\", &hll_resource) ==
FAILURE) {\\ RETURN_NULL(); \\ goto cleanup; \\ }\\ if ((hll = (robj
\*)zend_fetch_resource(Z_RES_P(hll_resource),
PHP_HLL_DESCRIPTOR_RES_NAME, hll_descriptor)) == NULL) { \\
RETVAL_FALSE; \\ goto cleanup; \\ } #define HLL_OBJ_ARG_ONLY()\\ zval
\*object, \*hll_resource, rv; \\ robj \*hll; \\ if
(zend_parse_method_parameters(ZEND_NUM_ARGS(), getThis(), \"O\",
&object, hll_hyperloglog_ce) == FAILURE) { \\ RETVAL_FALSE; \\ goto
cleanup; \\ } \\ zend_object \*zobject; \\ zend_parse_arg_obj(object,
&zobject, hll_hyperloglog_ce , true);\\ hll_resource =
zend_read_property(hll_hyperloglog_ce, zobject, ZEND_STRL(\"hll\"), 0,
&rv); \\ if ((hll = (robj \*)zend_fetch_resource(Z_RES_P(hll_resource),
PHP_HLL_DESCRIPTOR_RES_NAME, hll_descriptor)) == NULL ) { \\
RETVAL_FALSE; \\ goto cleanup; \\ } #define HLL_OBJ_GET_RESOURCE(V, O)
\\ do { \\ zval rv; \\ zend_object \*zobject; \\ zend_parse_arg_obj((O),
&zobject, hll_hyperloglog_ce , true);\\ zval \*hll_resource =
zend_read_property(hll_hyperloglog_ce, (zobject), ZEND_STRL(\"hll\"), 0,
&rv); \\ (V) = (robj \*) zend_fetch_resource(Z_RES_P(hll_resource),
PHP_HLL_DESCRIPTOR_RES_NAME, hll_descriptor); \\ } while(0); #ifndef
PHP_FE_END #define PHP_FE_END {NULL, NULL, NULL} #endif /\* }}} \*/ #if
PHP_MAJOR_VERSION == 7 #if PHP_MINOR_VERSION \< 4 static
zend_always_inline zend_bool try_convert_to_string(zval \*op) { if
(Z_TYPE_P(op) == IS_STRING) { return 1; } convert_to_string(op); return
1; } #endif #endif static int hll_descriptor; static zend_class_entry
\*hll_hyperloglog_ce; static zend_class_entry
\*hll_hyperloglogexception_ce; /\* {{{ Helpers \*/ static int
php_hll_create(INTERNAL_FUNCTION_PARAMETERS, robj \*\*hll, zend_bool
allow_sparse) { int ret = FAILURE; \*hll = hllCreate(); if (\*hll ==
NULL) { php_error_docref(NULL, E_ERROR, \"HLL could not be created\");
RETVAL_FALSE; goto cleanup; } if (!allow_sparse) { if
(hllSparseToDense(\*hll) != HLL_OK) { hllFree(\*hll);
php_error_docref(NULL, E_ERROR, \"HLL could not be converted to
dense\"); RETVAL_FALSE; goto cleanup; } } ret = SUCCESS; cleanup: return
ret; } static void php_hll_descriptor_dtor(zend_resource \*rsrc) { robj
\*hll = (robj \*)rsrc-\>ptr; hllFree(hll); } static int
php_hll_serialize(zval \*object, unsigned char \*\*buffer, size_t
\*buf_len, zend_serialize_data \*data) { robj \*hll = NULL;
HLL_OBJ_GET_RESOURCE(hll, object); smart_str buf = {0}; zval zv;
php_serialize_data_t serialize_data = (php_serialize_data_t) data;
PHP_VAR_SERIALIZE_INIT(serialize_data); sds raw = hllRaw(hll);
ZVAL_STRINGL(&zv, raw, sdslen(raw)); php_var_serialize(&buf, &zv,
&serialize_data); sdsfree(raw);
PHP_VAR_SERIALIZE_DESTROY(serialize_data); \*buffer = (unsigned char \*)
estrndup(ZSTR_VAL(buf.s), ZSTR_LEN(buf.s)); \*buf_len = ZSTR_LEN(buf.s);
zend_string_release(buf.s); return SUCCESS; } static int
php_hll_unserialize(zval \*object, zend_class_entry \*ce, const unsigned
char \*buf, size_t buf_len, zend_unserialize_data \*data) { // This
imitates gmp_unserialize. int retval = SUCCESS; zval zv; sds hll_str =
NULL; robj \*hll = NULL; const unsigned char \*p, \*max;
php_unserialize_data_t unserialize_data = (php_unserialize_data_t) data;
PHP_VAR_UNSERIALIZE_INIT(unserialize_data); p = buf; max = buf +
buf_len; if (!php_var_unserialize(&zv, &p, max, &unserialize_data) \|\|
Z_TYPE(zv) != IS_STRING ) { zend_throw_exception(NULL, \"Could not
unserialize HLL\", 0); goto fail; } hll_str = sdsnewlen(Z_STRVAL(zv),
Z_STRLEN(zv)); if (hllLoad(&hll, hll_str) == FAILURE) {
zend_throw_exception(NULL, \"Could not create HLL from unserialized
string\", 0); goto fail; } object_init_ex(object, hll_hyperloglog_ce);
zend_resource \*res = zend_register_resource(hll, hll_descriptor);
add_property_resource(object, \"hll\", res); goto cleanup; fail: retval
= FAILURE; cleanup: PHP_VAR_UNSERIALIZE_DESTROY(unserialize_data);
sdsfree(hll_str); return retval; } static int php_hll_from_zval(zval
\*in, robj \*\*out) { int ret = SUCCESS; if (Z_TYPE_P(in) ==
IS_RESOURCE) { if ((\*out = (robj \*) zend_fetch_resource(Z_RES_P(in),
PHP_HLL_DESCRIPTOR_RES_NAME, hll_descriptor)) == NULL) { goto fail; } }
else if (Z_TYPE_P(in) == IS_OBJECT) { if
(!instanceof_function(Z_OBJCE_P(in), hll_hyperloglog_ce)) {
php_error_docref(NULL, E_WARNING, \"Supplied argument is not a valid
HyperLogLog class\"); goto fail; } zval rv; zend_object \*zobject;
zend_parse_arg_obj(in, &zobject, hll_hyperloglog_ce , true); zval
\*hll_resource = zend_read_property(hll_hyperloglog_ce, zobject,
ZEND_STRL(\"hll\"), 0, &rv); if ((\*out = (robj
\*)zend_fetch_resource(Z_RES_P(hll_resource),
PHP_HLL_DESCRIPTOR_RES_NAME, hll_descriptor)) == NULL) { goto fail; } }
else { php_error_docref(NULL, E_WARNING, \"Supplied argument is not a
valid HyperLogLog resource or HyperLogLog class\"); goto fail; } if
(\*out == NULL) { php_error_docref(NULL, E_WARNING, \"Could not fetch
HyperLogLog\"); goto fail; } goto cleanup; fail: ret = FAILURE; cleanup:
return ret; } static int
php_hll_array_to_list(INTERNAL_FUNCTION_PARAMETERS, HashTable \*in, hll
\*\*out) { int ret = FAILURE; int i = 0; hll \*sources = \*out; zval
\*current; ZEND_HASH_FOREACH_VAL(in, current) { if
(php_hll_from_zval(current, &sources\[i++\]) == FAILURE) { goto fail; }
} ZEND_HASH_FOREACH_END(); ret = SUCCESS; goto cleanup; fail:
RETVAL_FALSE; cleanup: return ret; } static int
php_hll_args_to_list(INTERNAL_FUNCTION_PARAMETERS, zval \*args, int
sources_len, hll \*\*sources_in) { int ret = FAILURE; int i = 0; hll
\*sources = NULL; sources = \*sources_in; for (i = 0; i \< sources_len;
i++) { if (php_hll_from_zval(&args\[i\], &sources\[i\]) == FAILURE) {
goto fail; } } ret = SUCCESS; goto cleanup; fail: RETVAL_FALSE; cleanup:
return ret; } static int php_hll_info(INTERNAL_FUNCTION_PARAMETERS, robj
\*hll) { array_init(return_value); uint8_t type = ((struct hllhdr
\*)hll-\>ptr)-\>encoding; if (type == HLL_DENSE)
add_assoc_string(return_value, \"encoding\", \"dense\"); else if (type
== HLL_SPARSE) add_assoc_string(return_value, \"encoding\", \"sparse\");
else add_assoc_string(return_value, \"encoding\", \"unknown\"); return
SUCCESS; } static int php_hll_add(INTERNAL_FUNCTION_PARAMETERS, robj
\*hll, zval \*data, int \*updated) { int ret = FAILURE; char
\*\*add_strings = NULL; int add_idx = 0; int i = 0; switch
(Z_TYPE_P(data)) { case IS_NULL: case IS_TRUE: case IS_FALSE: case
IS_LONG: case IS_DOUBLE: case IS_STRING: case IS_OBJECT: ; zval
duplicate = \*data; zval_copy_ctor(&duplicate); if
(!try_convert_to_string(&duplicate)) { zval_dtor(&duplicate); goto
cleanup; } { sds input = sdsnew(Z_STRVAL(duplicate)); \*updated =
pfAdd(hll, input); sdsfree(input); } zval_dtor(&duplicate); if
(\*updated == HLL_ERR) { php_error_docref(NULL, E_WARNING, \"Could not
add element to HyperLogLog\"); } ret = SUCCESS; break; case IS_ARRAY: ;
int cnt = zend_hash_num_elements(Z_ARRVAL_P(data)); zval \*current;
add_strings = ecalloc(cnt + 1, sizeof(char \*));
ZEND_HASH_FOREACH_VAL(Z_ARRVAL_P(data), current) { switch
(Z_TYPE_P(current)) { case IS_NULL: case IS_TRUE: case IS_FALSE: case
IS_LONG: case IS_DOUBLE: case IS_STRING: case IS_OBJECT: ; zval
duplicate = \*current; zval_copy_ctor(&duplicate); if
(!try_convert_to_string(&duplicate)) { zval_dtor(&duplicate); goto
cleanup; } add_strings\[add_idx++\] = sdsnew(Z_STRVAL(duplicate));
zval_dtor(&duplicate); break; default: php_error_docref(NULL, E_WARNING,
\"Invalid type\"); goto cleanup; } } ZEND_HASH_FOREACH_END(); \*updated
= pfAddMany(hll, add_strings, cnt); if (\*updated == HLL_ERR) {
php_error_docref(NULL, E_WARNING, \"Could not add element to
HyperLogLog\"); } ret = SUCCESS; break; default: php_error_docref(NULL,
E_WARNING, \"Argument could not be converted to string\"); } cleanup: if
(add_strings) { for (i = 0; i \< add_idx; i++) {
sdsfree(add_strings\[i\]); } efree(add_strings); } return ret; } static
int php_hll_load(INTERNAL_FUNCTION_PARAMETERS, robj \*\*hll, char
\*input, size_t input_len) { int ret = FAILURE; sds input_sds =
sdsnewlen(input, input_len); int res = hllLoad(hll, input_sds); if
(\*hll == NULL \|\| res != HLL_OK) { if (\*hll != NULL) hllFree(\*hll);
php_error_docref(NULL, E_WARNING, \"Supplied HLL dump was invalid\");
RETVAL_FALSE; goto cleanup; } ret = SUCCESS; cleanup: if (input_sds !=
NULL) sdsfree(input_sds); return ret; } /\* }}} \*/ /\* {{{ proto void
HyperLogLog::\_\_construct(\[bool allowSparse = false\]) \* proto void
HyperLogLog::\_\_construct(string hllDump) \* proto void
HyperLogLog::\_\_construct(array hllsToMerge) \*/
PHP_METHOD(HyperLogLog, \_\_construct) { zval \*object = NULL; zval
\*input = NULL; robj \*hll_obj = NULL; hll \*hll_sources = NULL; int
sources_len = 0; zend_error_handling error_handling;
zend_replace_error_handling(EH_THROW, hll_hyperloglogexception_ce,
&error_handling); if (zend_parse_method_parameters(ZEND_NUM_ARGS(),
getThis(), \"O\|z\", &object, hll_hyperloglog_ce, &input) == FAILURE) {
RETVAL_FALSE; goto cleanup; } int is_null = input == NULL \|\|
Z_TYPE_P(input) == IS_NULL; if (is_null \|\| Z_TYPE_P(input) == IS_TRUE
\|\| Z_TYPE_P(input) == IS_FALSE) { zend_bool allow_sparse = is_null ? 0
: Z_TYPE_P(input) == IS_TRUE; if
(php_hll_create(INTERNAL_FUNCTION_PARAM_PASSTHRU, &hll_obj,
allow_sparse) != SUCCESS) { goto fail; } } else if (Z_TYPE_P(input) ==
IS_STRING) { if (php_hll_load(INTERNAL_FUNCTION_PARAM_PASSTHRU,
&hll_obj, Z_STRVAL_P(input), Z_STRLEN_P(input)) != SUCCESS) { goto fail;
} } else if (Z_TYPE_P(input) == IS_ARRAY) { HashTable \*hll_ht =
Z_ARRVAL_P(input); sources_len = zend_hash_num_elements(hll_ht);
hll_sources = emalloc(sizeof(hll) \* sources_len); if
(php_hll_array_to_list(INTERNAL_FUNCTION_PARAM_PASSTHRU, hll_ht,
&hll_sources) != SUCCESS) { goto fail; } if
(php_hll_create(INTERNAL_FUNCTION_PARAM_PASSTHRU, &hll_obj, 0) !=
SUCCESS) { goto fail; } if (pfMerge(hll_obj, hll_sources, sources_len)
!= HLL_OK) { php_error_docref(NULL, E_WARNING, \"Expected array or
resource\"); goto fail; } } zend_resource \*res =
zend_register_resource(hll_obj, hll_descriptor);
add_property_resource(object, \"hll\", res); goto cleanup; fail:
RETVAL_FALSE; cleanup: zend_restore_error_handling(&error_handling);
efree(hll_sources); return; } /\* }}} \*/ /\* {{{ proto resource
hll_create(\[bool allowSparse = false\]) \*/ PHP_FUNCTION(hll_create) {
robj \*hll; zend_bool allow_sparse = 0; if
(zend_parse_parameters(ZEND_NUM_ARGS(), \"\|b\", &allow_sparse) ==
FAILURE) { RETVAL_FALSE; goto cleanup; } if
(php_hll_create(INTERNAL_FUNCTION_PARAM_PASSTHRU, &hll, allow_sparse) !=
SUCCESS) { RETVAL_FALSE; goto cleanup; }
RETURN_RES(zend_register_resource(hll, hll_descriptor)); cleanup:
return; } /\* }}} \*/ /\* {{{ proto HyperLogLog HyperLogLog::merge (
mixed \$hyperLogLog \[ , mixed \$\... \]) \* proto HyperLogLog
HyperLogLog::merge ( array \$hyperLogLogs ) \*/ PHP_METHOD(HyperLogLog,
merge) { int argc = 0; zval \*args = NULL; hll \*hll_sources = NULL; int
sources_len = 0; zval \*object, \*hll_resource, rv; if
(zend_parse_method_parameters(ZEND_NUM_ARGS(), getThis(), \"O+\",
&object, hll_hyperloglog_ce, &args, &argc) == FAILURE) { goto cleanup; }
robj \*hll_target = NULL; zend_object \*zobject;
zend_parse_arg_obj(object, &zobject, hll_hyperloglog_ce , true);
hll_resource = zend_read_property(hll_hyperloglog_ce, zobject,
ZEND_STRL(\"hll\"), 0, &rv); if ((hll_target = (robj
\*)zend_fetch_resource(Z_RES_P(hll_resource),
PHP_HLL_DESCRIPTOR_RES_NAME, hll_descriptor)) == NULL) { RETURN_FALSE; }
if (hll_target == NULL) { php_error_docref(NULL, E_ERROR, \"HLL could
not be retrieved\"); goto fail; } if (argc == 1 && Z_TYPE_P(args) ==
IS_ARRAY) { HashTable \*hll_ht = Z_ARRVAL(args\[0\]); sources_len =
zend_hash_num_elements(hll_ht) + 1; hll_sources = emalloc(sizeof(hll) \*
sources_len); if
(php_hll_array_to_list(INTERNAL_FUNCTION_PARAM_PASSTHRU, hll_ht,
&hll_sources) != SUCCESS) { goto fail; } } else { sources_len = argc +
1; hll_sources = emalloc(sizeof(hll) \* sources_len); if
(php_hll_args_to_list(INTERNAL_FUNCTION_PARAM_PASSTHRU, args, argc,
&hll_sources) != SUCCESS) { goto fail; } } if (sources_len \< 2) {
zend_wrong_param_count(); goto fail; } hll_sources\[sources_len - 1\] =
hll_target; if (pfMerge(hll_target, hll_sources, sources_len) != HLL_OK)
{ php_error_docref(NULL, E_WARNING, \"Expected array or resource\");
goto fail; } RETVAL_ZVAL(getThis(), 1, 0); goto cleanup; fail:
RETVAL_FALSE; cleanup: efree(hll_sources); return; } /\* }}} \*/ /\* {{{
proto resource hll_merge( mixed \$hyperLogLog1 , mixed \$hyperLogLog2 \[
, mixed \$\... \]) \* proto resource hll_merge( array \$hyperLogLogs )
\*/ PHP_FUNCTION(hll_merge) { int argc = 0; zval \*args = NULL; hll
\*hll_sources = NULL; int sources_len = 0; if
(zend_parse_parameters(ZEND_NUM_ARGS(), \"+\", &args, &argc) == FAILURE)
{ goto cleanup; } robj \*hll_target = NULL; hll_target = hllCreate(); if
(hll_target == NULL) { php_error_docref(NULL, E_WARNING, \"HLL could not
be created\"); goto fail; } if (argc == 1 && Z_TYPE_P(args) == IS_ARRAY)
{ HashTable \*hll_ht = Z_ARRVAL(args\[0\]); sources_len =
zend_hash_num_elements(hll_ht); hll_sources = emalloc(sizeof(hll) \*
sources_len); if
(php_hll_array_to_list(INTERNAL_FUNCTION_PARAM_PASSTHRU, hll_ht,
&hll_sources) != SUCCESS) { goto fail; } } else { sources_len = argc;
hll_sources = emalloc(sizeof(hll) \* argc); if
(php_hll_args_to_list(INTERNAL_FUNCTION_PARAM_PASSTHRU, args, argc,
&hll_sources) != SUCCESS) { goto fail; } } if (sources_len \< 2) {
zend_wrong_param_count(); goto fail; } if (pfMerge(hll_target,
hll_sources, sources_len) != HLL_OK) { php_error_docref(NULL, E_WARNING,
\"Expected array or resource\"); goto fail; }
RETURN_RES(zend_register_resource(hll_target, hll_descriptor)); goto
cleanup; fail: RETVAL_FALSE; cleanup: efree(hll_sources); return; } /\*
}}} \*/ /\* {{{ proto HyperLogLog HyperLogLog::add( scalar \$value , \[
bool &\$updated \]) \* proto HyperLogLog HyperLogLog::add( array
\$values , \[ bool &\$updated \]) \*/
ZEND_BEGIN_ARG_INFO_EX(ai_HyperLogLog_add, 0, 0, 1) ZEND_ARG_INFO(0,
input) ZEND_ARG_INFO(1, updated) ZEND_END_ARG_INFO()
PHP_METHOD(HyperLogLog, add) { zval \*object, \*data, rv; robj \*hll;
int updated = 0; zend_error_handling errorh; zval \*upd_arg = NULL;
zend_replace_error_handling(EH_THROW, hll_hyperloglogexception_ce,
&errorh); if (zend_parse_method_parameters(ZEND_NUM_ARGS(), getThis(),
\"Oz\|z/\", &object, hll_hyperloglog_ce, &data, &upd_arg) == FAILURE) {
goto fail; } zend_object \*zobject; zend_parse_arg_obj(object, &zobject,
hll_hyperloglog_ce , true); zval \*hll_resource =
zend_read_property(hll_hyperloglog_ce, zobject, ZEND_STRL(\"hll\"), 0,
&rv); if ((hll = (robj \*)zend_fetch_resource(Z_RES_P(hll_resource),
PHP_HLL_DESCRIPTOR_RES_NAME, hll_descriptor)) == NULL) { goto fail; } if
(php_hll_add(INTERNAL_FUNCTION_PARAM_PASSTHRU, hll, data, &updated) !=
SUCCESS) { goto fail; } if (upd_arg) { zval_ptr_dtor(upd_arg);
ZVAL_BOOL(upd_arg, updated); } RETVAL_ZVAL(getThis(), 1, 0); goto
cleanup; fail: RETVAL_FALSE; cleanup:
zend_restore_error_handling(&errorh); } /\* }}} \*/ /\* {{{ proto bool
hll_add ( resource \$hll , scalar \$value ) \* proto bool hll_add (
resource \$hll , array \$values ) \*/ PHP_FUNCTION(hll_add) { robj
\*hll; zval \*hll_resource; zval \*data; int updated = 0; if
(zend_parse_parameters(ZEND_NUM_ARGS(), \"rz\", &hll_resource, &data) ==
FAILURE) { RETURN_NULL(); } if ((hll = (robj
\*)zend_fetch_resource(Z_RES_P(hll_resource),
PHP_HLL_DESCRIPTOR_RES_NAME, hll_descriptor)) == NULL ) { goto cleanup;
} if (php_hll_add(INTERNAL_FUNCTION_PARAM_PASSTHRU, hll, data, &updated)
!= SUCCESS) { RETVAL_FALSE; goto cleanup; } cleanup: RETURN_BOOL(updated
== 1); } /\* }}} \*/ /\* {{{ proto int HyperLogLog::count( void ) \*/
PHP_METHOD(HyperLogLog, count) { HLL_OBJ_ARG_ONLY(); uint64_t count =
pfCount(hll); RETVAL_LONG(count); fail: cleanup: return; } /\* }}} \*/
/\* {{{ proto int hll_count ( mixed \$hll \[ , mixed \$\... \]) \*/
PHP_FUNCTION(hll_count) { hll \*hll_sources = NULL; zval \*args = NULL;
int argc = 0; int i = 0; if (zend_parse_parameters(ZEND_NUM_ARGS(),
\"+\", &args, &argc) == FAILURE) { goto cleanup; } hll_sources =
emalloc(sizeof(hll) \* argc); if
(php_hll_args_to_list(INTERNAL_FUNCTION_PARAM_PASSTHRU, args, argc,
&hll_sources) != SUCCESS) { RETVAL_FALSE; goto cleanup; } if (argc == 1)
{ uint64_t count = pfCount(hll_sources\[0\]); RETVAL_LONG(count); } else
if (argc \> 1) { uint64_t count = pfCountMerged(hll_sources, argc);
RETVAL_LONG(count); } else { zend_wrong_param_count(); } cleanup:
efree(hll_sources); } /\* }}} \*/ /\* {{{ proto HyperLogLog
HyperLogLog::promote ( void ) \*/ PHP_METHOD(HyperLogLog, promote) {
HLL_OBJ_ARG_ONLY(); if (hllSparseToDense(hll) != HLL_OK) {
php_error_docref(NULL, E_WARNING, \"HLL could not be promoted\"); }
RETVAL_ZVAL(getThis(), 1, 0); cleanup: return; } /\* }}} \*/ /\* {{{
proto void hll_promote ( resource \$hll ) \*/ PHP_FUNCTION(hll_promote)
{ HLL_ARG_ONLY(); if (hllSparseToDense(hll) != HLL_OK) {
php_error_docref(NULL, E_WARNING, \"HLL could not be promoted\"); }
cleanup: RETURN_NULL(); } /\* }}} \*/ /\* {{{ proto array
HyperLogLog::info ( void ) \*/ PHP_METHOD(HyperLogLog, info) {
HLL_OBJ_ARG_ONLY(); if (php_hll_info(INTERNAL_FUNCTION_PARAM_PASSTHRU,
hll) != SUCCESS) { php_error_docref(NULL, E_WARNING, \"Could not fetch
info\"); RETVAL_FALSE; goto cleanup; } cleanup: return; } /\* }}} \*/
/\* {{{ proto array hll_info ( resource \$hll ) \*/
PHP_FUNCTION(hll_info) { HLL_ARG_ONLY(); if
(php_hll_info(INTERNAL_FUNCTION_PARAM_PASSTHRU, hll) != SUCCESS) {
php_error_docref(NULL, E_WARNING, \"Could not fetch info\");
RETVAL_FALSE; goto cleanup; } cleanup: return; } /\* }}} \*/ /\* {{{
proto string HyperLogLog::dump ( void ) \*/ PHP_METHOD(HyperLogLog,
dump) { HLL_OBJ_ARG_ONLY(); sds raw = hllRaw(hll);
ZVAL_STRINGL(return_value, raw, sdslen(raw)); sdsfree(raw); cleanup:
return; } /\* }}} \*/ /\* {{{ proto string hll_dump ( resource \$hll )
\*/ PHP_FUNCTION(hll_dump) { HLL_ARG_ONLY(); sds raw = hllRaw(hll);
ZVAL_STRINGL(return_value, raw, sdslen(raw)); sdsfree(raw); cleanup:
return; } /\* }}} \*/ /\* {{{ proto resource hll_load ( string \$hllDump
) \*/ PHP_FUNCTION(hll_load) { char \*input; size_t input_len; if
(zend_parse_parameters(ZEND_NUM_ARGS(), \"s\", &input, &input_len) ==
FAILURE) { RETURN_NULL(); } robj \*hll = NULL; if
(php_hll_load(INTERNAL_FUNCTION_PARAM_PASSTHRU, &hll, input, input_len)
!= SUCCESS) { RETVAL_FALSE; goto cleanup; }
RETURN_RES(zend_register_resource(hll, hll_descriptor)); cleanup:
return; } /\* }}} \*/ /\* {{{ argument information \*/
ZEND_BEGIN_ARG_INFO_EX(arginfo_HyperLogLog\_\_construct, 0, 0, 1)
ZEND_ARG_INFO(0, hllsToMerge) ZEND_END_ARG_INFO()
ZEND_BEGIN_ARG_INFO_EX(arginfo_HyperLogLog_merge, 0, 0, 1)
ZEND_ARG_INFO(0, hyperLogLogs) ZEND_END_ARG_INFO()
ZEND_BEGIN_ARG_INFO_EX(arginfo_HyperLogLog_count, 0, 0, 0)
ZEND_END_ARG_INFO() ZEND_BEGIN_ARG_INFO_EX(arginfo_HyperLogLog_promote,
0, 0, 0) ZEND_END_ARG_INFO()
ZEND_BEGIN_ARG_INFO_EX(arginfo_HyperLogLog_info, 0, 0, 0)
ZEND_END_ARG_INFO() ZEND_BEGIN_ARG_INFO_EX(arginfo_HyperLogLog_dump, 0,
0, 0) ZEND_END_ARG_INFO() /\* }}} \*/ const static zend_function_entry
hll_hyperloglog_methods\[\] = { PHP_ME(HyperLogLog, \_\_construct,
arginfo_HyperLogLog\_\_construct, ZEND_ACC_CTOR \| ZEND_ACC_PUBLIC)
PHP_ME(HyperLogLog, merge, arginfo_HyperLogLog_merge, ZEND_ACC_PUBLIC)
PHP_ME(HyperLogLog, add, ai_HyperLogLog_add, ZEND_ACC_PUBLIC)
PHP_ME(HyperLogLog, count, arginfo_HyperLogLog_count, ZEND_ACC_PUBLIC)
PHP_ME(HyperLogLog, promote, arginfo_HyperLogLog_promote,
ZEND_ACC_PUBLIC) PHP_ME(HyperLogLog, info, arginfo_HyperLogLog_info,
ZEND_ACC_PUBLIC) PHP_ME(HyperLogLog, dump, arginfo_HyperLogLog_dump,
ZEND_ACC_PUBLIC) PHP_FE_END }; const static zend_function_entry
hll_hyperloglogexception_methods\[\] = { PHP_FE_END }; /\* {{{ argument
information \*/ ZEND_BEGIN_ARG_INFO_EX(arginfo_hll_create, 0, 0, 1)
ZEND_ARG_INFO(0, allowSparse) ZEND_END_ARG_INFO()
ZEND_BEGIN_ARG_INFO_EX(arginfo_hll_add, 0, 0, 2) ZEND_ARG_INFO(0, hll)
ZEND_ARG_INFO(0, values) ZEND_END_ARG_INFO()
ZEND_BEGIN_ARG_INFO_EX(arginfo_hll_merge, 0, 0, 1) ZEND_ARG_INFO(0,
hyperLogLogs) ZEND_END_ARG_INFO()
ZEND_BEGIN_ARG_INFO_EX(arginfo_hll_count, 0, 0, 1) ZEND_ARG_INFO(0, hll)
ZEND_END_ARG_INFO() ZEND_BEGIN_ARG_INFO_EX(arginfo_hll_promote, 0, 0, 1)
ZEND_ARG_INFO(0, hll) ZEND_END_ARG_INFO()
ZEND_BEGIN_ARG_INFO_EX(arginfo_hll_info, 0, 0, 1) ZEND_ARG_INFO(0, hll)
ZEND_END_ARG_INFO() ZEND_BEGIN_ARG_INFO_EX(arginfo_hll_dump, 0, 0, 1)
ZEND_ARG_INFO(0, hll) ZEND_END_ARG_INFO()
ZEND_BEGIN_ARG_INFO_EX(arginfo_hll_load, 0, 0, 1) ZEND_ARG_INFO(0,
hllDump) ZEND_END_ARG_INFO() /\* }}} \*/ static zend_function_entry
php_hll_functions\[\] = { PHP_FE(hll_create, arginfo_hll_create)
PHP_FE(hll_add, arginfo_hll_add) PHP_FE(hll_merge, arginfo_hll_merge)
PHP_FE(hll_count, arginfo_hll_count) PHP_FE(hll_promote,
arginfo_hll_promote) PHP_FE(hll_info, arginfo_hll_info) PHP_FE(hll_dump,
arginfo_hll_dump) PHP_FE(hll_load, arginfo_hll_load) PHP_FE_END };
zend_module_entry hll_module_entry = { STANDARD_MODULE_HEADER,
PHP_HLL_EXTNAME, php_hll_functions, PHP_MINIT(hll), /\* MINIT \*/ NULL,
/\* MSHUTDOWN \*/ NULL, /\* RINIT \*/ NULL, /\* RSHUTDOWN \*/ NULL, /\*
MINFO \*/ PHP_HLL_EXTVER, STANDARD_MODULE_PROPERTIES, };
PHP_MINIT_FUNCTION(hll) { zend_class_entry ce = {0}; hll_descriptor =
zend_register_list_destructors_ex( php_hll_descriptor_dtor, NULL,
PHP_HLL_DESCRIPTOR_RES_NAME, module_number); hll_ce: {
INIT_CLASS_ENTRY(ce, \"HyperLogLog\", hll_hyperloglog_methods);
hll_hyperloglog_ce = zend_register_internal_class(&ce);
hll_hyperloglog_ce-\>serialize = php_hll_serialize;
hll_hyperloglog_ce-\>unserialize = php_hll_unserialize;
hll_hyperloglog_ce-\>clone = NULL;
zend_declare_property_null(hll_hyperloglog_ce, ZEND_STRL(\"hll\"),
ZEND_ACC_PUBLIC); } hll_exception: { INIT_CLASS_ENTRY(ce,
\"HyperLogLogException\", hll_hyperloglogexception_methods);
hll_hyperloglogexception_ce = zend_register_internal_class_ex(&ce,
zend_exception_get_default()); hll_hyperloglogexception_ce-\>ce_flags
\|= ZEND_ACC_FINAL; } return SUCCESS; } #ifdef COMPILE_DL_HLL
ZEND_GET_MODULE(hll) #endif

# Laravel Upgrade Changes

## **Laravel 5.2 to 5.3**

Shifting of Call back Parameters Passed to the functions **Arr::first**
**Arr::last** and **Arr::where**

key and value passed to the callback are changed to value and
key.Arr::first(\$array, function (\$value, \$key) { return !
is_null(\$value); });

The `make:console` command has been renamed to `make:command`.

Shifting of Call back Parameters Passed to the `Collection Class`
functions `first`, `last`, and `contains`

key and value passed to the callback are changed to value and
key.\$collection-\>first(function (\$value, \$key) { return !
is_null(\$value); });

#### Collection `where` Comparison Methods Are \"Loose\" By Default

use the whereStrict method for strict comparison instead

A collection\'s `where` method now performs a \"loose\" comparison by
default instead of a strict comparison. If you would like to perform a
strict comparison, you may use the `whereStrict` method.

Due to this change, the `whereLoose` method was removed from the
collection class.

The `where` method also no longer accepts a third parameter to indicate
\"strictness\". You should explicitly call either `where` or
`whereStrict` depending on your application\'s needs.

The [[fluent query
builder]{.underline}](https://laravel.com/docs/5.3/queries) now returns
`Illuminate\Support\Collection` instances instead of plain arrays

use all method maintain backwards compatibility

If you do not want to migrate your query builder results to `Collection`
instances, you may chain the `all` method onto your calls to the query
builder\'s `get` or `pluck` methods. This will return a plain PHP array
of the results, allowing you to maintain backwards compatibility:

\$users = DB::table(\'users\')-\>get()-\>all(); \$usersIds =
DB::table(\'users\')-\>pluck(\'id\')-\>all();

There are some deprecated feathers in Eloquent Scoping .Please go to

[https://laravel.com/docs/5.3/upgrade](https://laravel.com/docs/5.3/upgrade){card-appearance="inline"}

## **Laravel 5.3 to 5.4**

#### In Laravel 5.4, inline content passed to a section is automatically escaped:

\@section(\'title\', \$content)

If you would like to render unescaped content in a section, you must
declare the section using the traditional \"long form\" style:

\@section(\'title\') {!! \$content !!} \@stop

The behavior of the Collection `every` method has been moved to the
`nth` method to match the method name defined by Lodash.

Calling `$collection->random(1)` will now return a new collection
instance with one item. Previously, this would return a single object.
This method will only return a single object if no arguments are
supplied.

When passing an array as first argument to the `orWhere` method, the
inner conditions now use `OR` between each array element:

\$query-\>orWhere(\[\'a\' =\> 1, \'b\' =\> 2\]) OR (a = 1 AND b = 2) //
Prior Behavior\... OR (a = 1 OR b = 2) // New Behavior..

The `date` cast now converts the column to a `Carbon` object and calls
the `startOfDay` method on the object. If you would like to preserve the
time portion of the date, you should use the `datetime` cast.

#### BelongsToMany `setJoin`

The `setJoin` method has been renamed to `performJoin`.

#### BelongsToMany `getRelatedIds`

The `getRelatedIds` method has been renamed to `allRelatedIds`.

#### Has One / Many `createMany`

The `createMany` method of a `hasOne` or `hasMany` relationship now
returns a collection object instead of an array.

#### Has One / Many `getPlainForeignKey`

The `getPlainForeignKey` method has been renamed to `getForeignKeyName`.

Related models will now use the same connection as the parent model. For
example, if you execute a query like:

User::on(\'example\')-\>with(\'posts\');

Eloquent will query the posts table on the `example` connection instead
of the default database connection. If you want to read the `posts`
relationship from the default connection, you should to explicitly set
the model\'s connection to your application\'s default connection.

The query builder `chunk` method now requires an `orderBy` clause, which
provides consistency with the `each` method. An exception will be thrown
if an `orderBy` clause is not supplied.

DB::table(\'users\')-\>orderBy(\'id\')-\>chunk(100, function (\$users) {
foreach (\$users as \$user) { // } });

The Eloquent query builder `chunk` method will automatically apply an
`orderBy` clause on the model\'s primary key if one is not supplied.

The `Model::create` & `Model::forceCreate` methods have been moved to
the `Illuminate\Database\Eloquent\Builder` class in order to provide
better support for creating models on multiple connections

However, if you are extending these methods in your own models, you will
need to modify your implementation to call the `create` method on the
builder. For example:

public static function create(array \$attributes = \[\]) { \$model =
static::query()-\>create(\$attributes); // \... return \$model; }

The `getUri` method of the `Illuminate\Routing\Route` class has been
removed. You should use the `uri` method instead.

The `getMethods` method of the `Illuminate\Routing\Route` class has been
removed. You should use the `methods` method instead.

The `getParameter` method of the `Illuminate\Routing\Route` class has
been removed. You should use the `parameter` method instead.

The `getPath` method of the `Illuminate\Routing\Route` class has been
removed. You should use the `uri` method instead.

The `forceSchema` method of the `Illuminate\Routing\UrlGenerator` class
has been renamed to `forceScheme`.

## **Laravel 5.4 to 5.5**

#### Auto-Loading Commands

In Laravel 5.5, Artisan can automatically discover commands so that you
do not have to manually register them in your kernel. To take advantage
of this new feature, you should add the following line to the `commands`
method of your `App\Console\Kernel` class:

\$this-\>load(\_\_DIR\_\_.\'/Commands\');

Any `fire` methods present on your Artisan commands should be renamed to
`handle`.

#### The `optimize` Command

With recent improvements to PHP op-code caching, the `optimize` Artisan
command is no longer needed. You should remove any references to this
command from your deployment scripts as it will be removed in a future
release of Laravel.

#### Model `$events` Property

The `$events` property on your models should be renamed to
`$dispatchesEvents`. This change was made because of a high number of
users needing to define an `events` relationship, which caused a
conflict with the old property name.

#### Soft Deleted Models

When deleting a \"soft deleted\" model, the `exists` property on the
model will remain `true`.

## **Laravel 5.5 to 5.6**

#### The `optimize` Command

The previously deprecated `optimize` Artisan command has been removed.
With recent improvements to PHP itself including the OPcache, the
`optimize` command no longer provides any relevant performance benefit.
Therefore, you may remove `php artisan optimize` from the `scripts`
within your `composer.json` file.

#### HTML Entity Encoding

In previous versions of Laravel, Blade (and the `e` helper) would not
double encode HTML entities. This was not the default behavior of the
underlying `htmlspecialchars` function and could lead to unexpected
behavior when rendering content or passing in-line JSON content to
JavaScript frameworks.

In Laravel 5.6, Blade and the `e` helper will double encode special
characters by default. This brings these features into alignment with
the default behavior of the underlying `htmlspecialchars` PHP function.
If you would like to maintain the previous behavior of preventing double
encoding, you may use the `Blade::withoutDoubleEncoding` method:

\<?php namespace App\\Providers; use
Illuminate\\Support\\Facades\\Blade; use
Illuminate\\Support\\ServiceProvider; class AppServiceProvider extends
ServiceProvider { /\*\* \* Bootstrap any application services. \* \*
\@return void \*/ public function boot() {
Blade::withoutDoubleEncoding(); } }

#### The `e` Helper

In previous versions of Laravel, Blade (and the `e` helper) would not
double encode HTML entities. This was not the default behavior of the
underlying `htmlspecialchars` function and could lead to unexpected
behavior when rendering content or passing in-line JSON content to
JavaScript frameworks.

In Laravel 5.6, Blade and the `e` helper will double encode special
characters by default. This brings these features into alignment with
the default behavior of the underlying `htmlspecialchars` PHP function.
If you would like to maintain the previous behavior of preventing double
encoding, you may pass `false` as the second argument to the `e` helper:

\<?php echo e(\$string, false); ?\>

## **Laravel 5.6 to 5.7**

#### `svg` Directory Added

A new directory, `svg`, was added to the `public` directory. It contains
four svg files: `403.svg`, `404.svg`, `500.svg`, and `503.svg`, which
are displayed on their respective error pages.

You may get the files [[from
GitHub]{.underline}](https://github.com/laravel/laravel/tree/5.7/public/svg).

#### The `or` Operator

The Blade \"or\" operator has been removed in favor of PHP\'s built-in
`??` \"null coalesce\" operator, which has the same purpose and
functionality:

// Laravel 5.6\... {{ \$foo or \'default\' }} // Laravel 5.7\... {{
\$foo ?? \'default\' }}

### new `data` directory has been added to `storage/framework/cache`

A new `data` directory has been added to `storage/framework/cache`. You
should create this directory in your own application:

mkdir -p storage/framework/cache/data

Then, add a
[[.gitignore]{.underline}](https://github.com/laravel/laravel/blob/76369205c8715a4a8d0d73061aa042a74fd402dc/storage/framework/cache/data/.gitignore)
file to the newly created `data` directory:

cp storage/framework/cache/.gitignore
storage/framework/cache/data/.gitignore

Finally, ensure that the
[[storage/framework/cache/.gitignore]{.underline}](https://github.com/laravel/laravel/blob/76369205c8715a4a8d0d73061aa042a74fd402dc/storage/framework/cache/.gitignore)
file is updated as follows:

\*!data/!.gitignore

The query builder\'s `whereDate` method now converts `DateTime`
instances to `Y-m-d` format:

// previous behaviour - SELECT \* FROM \`table\` WHERE \`created_at\` \>
\'2018-08-01 13:00:00\' \$query-\>whereDate(\'created_at\', \'\>\',
Carbon::parse(\'2018-08-01 13:00:00\')); // current behaviour - SELECT
\* FROM \`table\` WHERE \`created_at\` \> \'2018-08-01\'
\$query-\>whereDate(\'created_at\', \'\>\', Carbon::parse(\'2018-08-01
13:00:00\'));

#### The `Route::redirect` Method

The `Route::redirect` method now returns a `302` HTTP status code
redirect. The `permanentRedirect` method has been added to allow `301`
redirects.

// Return a 302 redirect\... Route::redirect(\'/foo\', \'/bar\'); //
Return a 301 redirect\... Route::redirect(\'/foo\', \'/bar\', 301); //
Return a 301 redirect\... Route::permanentRedirect(\'/foo\', \'/bar\');

## **Laravel 5.7 to 5.8**

cache TTL Changes go to the anchor.

[https://laravel.com/docs/5.8/upgrade#cache-ttl-in-seconds](https://laravel.com/docs/5.8/upgrade#cache-ttl-in-seconds){card-appearance="inline"}

Laravel now supports both Carbon 1 and Carbon 2

therefore, Composer will try to upgrade to Carbon 2.0 if no other
compatibility issues with any other packages are detected. Please review
the [[migration guide for Carbon
2.0]{.underline}](https://carbon.nesbot.com/docs/#api-carbon-2).

#### Automatic Soft-Deleted Casting Of `deleted_at` Property

The `deleted_at` property [[will now be automatically
casted]{.underline}](https://github.com/laravel/framework/pull/26985) to
a `Carbon` instance when your Eloquent model uses the
`Illuminate\Database\Eloquent\SoftDeletes` trait. You can override this
behavior by writing your custom accessor for that property or by
manually adding it to the `casts` attribute:

protected \$casts = \[\'deleted_at\' =\> \'string\'\];

### [Environment Variable Parsing](https://laravel.com/docs/5.8/upgrade#environment-variable-parsing)

The [[phpdotenv]{.underline}](https://github.com/vlucas/phpdotenv)
package that is used to parse `.env` files has released a new major
version, which may impact the results returned from the `env` helper.
Specifically, the `#` character in an unquoted value will now be
considered a comment instead of part of the value:

Previous behavior:

ENV_VALUE=foo#bar env(\'ENV_VALUE\'); // foo#bar

New behavior:

ENV_VALUE=foo#barenv(\'ENV_VALUE\'); // foo

To preserve the previous behavior, you may wrap the environment values
in quotes:

ENV_VALUE=\"foo#bar\" env(\'ENV_VALUE\'); // foo#bar

For more information, please refer to the [[phpdotenv upgrade
guide]{.underline}](https://github.com/vlucas/phpdotenv/blob/master/UPGRADING.md).

#### [Prefer String And Array Classes Over Helpers](https://laravel.com/docs/5.8/upgrade#string-and-array-helpers)

All `array_*` and `str_*` global helpers [[have been
deprecated]{.underline}](https://github.com/laravel/framework/pull/26898).
You should use the `Illuminate\Support\Arr` and `Illuminate\Support\Str`
methods directly.

The impact of this change has been marked as `medium` since the helpers
have been moved to the new
[[laravel/helpers]{.underline}](https://github.com/laravel/helpers)
package which offers a backwards compatibility layer for all of the
global array and string functions.

If you choose to update your Laravel application\'s views to use the
class based methods, you should clear your compiled views which may
still be using the global helpers:

php artisan view:clear

#### Read-Only `env` Helper

Previously, the `env` helper could retrieve values from environment
variables which were changed at runtime. In Laravel 5.8, the `env`
helper treats environment variables as immutable. If you would like to
change an environment variable at runtime, consider using a
configuration value that can be retrieved using the `config` helper:

Previous behavior:

dump(env(\'APP_ENV\')); // local putenv(\'APP_ENV=staging\');
dump(env(\'APP_ENV\')); // staging

New behavior:

dump(env(\'APP_ENV\')); // local putenv(\'APP_ENV=staging\');
dump(env(\'APP_ENV\')); // local

**Laravel 5.8 to 6.x**

#### [Carbon 1.x No Longer Supported](https://laravel.com/docs/6.x/upgrade#carbon-support)

Carbon 1.x [[is no longer
supported]{.underline}](https://github.com/laravel/framework/pull/28683)
since it is nearing its maintenance end of life. Please upgrade your
application to Carbon 2.0.

#### [Declaration Of Primary Key Type](https://laravel.com/docs/6.x/upgrade#eloquent-primary-key-type)

Laravel 6.0 has received [[performance
optimizations]{.underline}](https://github.com/laravel/framework/pull/28153)
for integer key types. If you are using a string as your model\'s
primary key, you should declare the key type using the `$keyType`
property on your model:

/\*\* \* The \"type\" of the primary key ID. \* \* \@var string \*/
protected \$keyType = \'string\';

#### String & Array Helpers Package

All `str_` and `array_` helpers have been moved to the new
`laravel/helpers` Composer package and removed from the framework. If
desired, you may update all calls to these helpers to use the
`Illuminate\Support\Str` and `Illuminate\Support\Arr` classes.
Alternatively, you can add the new `laravel/helpers` package to your
application to continue using these helpers:

composer require laravel/helpers

If you choose to update your Laravel application\'s views to use the
class based methods, you should clear your compiled views which may
still be using the global helpers:

php artisan view:clear

#### [The](https://laravel.com/docs/6.x/upgrade#the-input-facade) `Input` Facade

The `Input` facade, which was primarily a duplicate of the `Request`
facade, has been removed. If you are using the `Input::get` method, you
should now call the `Request::input` method. All other calls to the
`Input` facade may simply be updated to use the `Request` facade.

# PHP Upgrade Docs

[https://www.php.net/manual/en/migration72.php](https://www.php.net/manual/en/migration72.php){card-appearance="inline"}

[https://www.php.net/manual/en/migration73.php](https://www.php.net/manual/en/migration73.php){card-appearance="inline"}

[https://www.php.net/manual/en/migration74.php](https://www.php.net/manual/en/migration74.php){card-appearance="inline"}

[https://www.php.net/manual/en/migration80.php](https://www.php.net/manual/en/migration80.php){card-appearance="inline"}
