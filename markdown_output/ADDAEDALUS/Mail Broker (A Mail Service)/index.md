Mail Broker is a secure and reliable email service, which helps to send
single and bulk emails with various options.

### Features

- SMTP connection helps you to send email from any server, especially
  local.

- It comes with a queue mechanism, specially designed to handle tons of
  email messages.

- Support bulk email messages.

- Customizable headers allow you to deal with `From Name`, `From Email`,
  `CC `& `BCC,` etc.

- Does support multiple attachments.

- Pull or push delivery.

- Schedule or delay delivery (customization required).

- Failed job handle capabilities.

- Supports Template/non-template-based approach (customization
  required).

### About

- Mail Broker is a simple mail service that uses the laravel mail
  feature.

- Mail Broker currently using `database` as a queue driver which can be
  change to `"null", "sync", "database", "beanstalkd", "sqs", "redis"`.

- To change the queue driver you can follow any of the below approaches.

  - in `.env` file (Recommended)\
    `QUEUE_DRIVER=redis`

  - in` config/queue.php `\
    `'default' => env('QUEUE_DRIVER', 'redis')`

- `database` queue driver comes with two tables I,e: `jobs` &
  `failed_jobs`

- The `jobs` table helps, to queue email messages for background
  sending.

- The `failed_jobs` helps, to queue failed email messages for background
  sending.

### Integration

#### Step 1: Get the `jobs` & `failed_jobs` table.

Note: you can follow any below approach

- Approach 1

  - Run `php artisan queue:table`. which will create a migration file
    for table `jobs`.

  - Run `php artisan queue:failed-table`. which will create a migration
    file for table `failed_jobs`.

  - Run `php artisan migrate`. which will run all of your outstanding
    migrations.

- Approach 2 (Recommended)

  - Run `php artisan queue:table`, which will create a migration file
    for table `jobs`.

  - Run `php artisan queue:failed-table`, which will create a migration
    file for table `failed_jobs`.

  - Create a folder called queue inside the `database/migrations`
    folder. Copy the newly created migrations files from the
    `database/migrations` folder to the
    `database/migrations/queue `folder.

  - Run `php artisan migrate --path=database/migrations/queue`.

- Approach 3 (Recommended)

  - Get `jobs` & `failed_jobs` table dump.

#### Step 2: Configuration

Add the below things to the `.env` file.

Note:

QUEUE_DRIVER=database MAIL_DRIVER=smtp MAIL_HOST=smtp.gmail.com
MAIL_PORT=465 MAIL_USERNAME=user@example.com MAIL_PASSWORD=password
MAIL_ENCRYPTION=SSL

#### Step 3

In your `controller`or `module`

`use App\Modules\Mail;`\
`Mail::sendMailFromLocal("user@example.com","Test Subject","Lorem Ipsum",$headers,$attachments);`

#### Step 4

Run `php artisan queue:listen `to a given queue and process the job.

Note: To re-send failed job Run` php artisan queue:failed`.

### API Documentation

+---------------+------------+--------------------+-----------------------------------------------------------+
| Parameter     | Required   | Data Type          | Description                                               |
+---------------+------------+--------------------+-----------------------------------------------------------+
| *to*          | *Yes*      | *String \| Array*  | - Specifies the receiver/receivers of the email           |
|               |            |                    |                                                           |
|               |            |                    | - Can send single and bulk emails.                        |
|               |            |                    |                                                           |
|               |            |                    | - Example:                                                |
|               |            |                    |                                                           |
|               |            |                    |   - `"user@example.com"`                                  |
|               |            |                    |                                                           |
|               |            |                    |   - `"user@example.com, anotheruser@example.com"`         |
|               |            |                    |                                                           |
|               |            |                    |   - `["user@example.com", "anotheruser@example.com"]`     |
+---------------+------------+--------------------+-----------------------------------------------------------+
| *subject*     | *Optional* | *String \| Null*   | - Specifies the subject of the email.                     |
+---------------+------------+--------------------+-----------------------------------------------------------+
| *message*     | *Optional* | *String \| Null*   | - Defines the message to be sent.                         |
+---------------+------------+--------------------+-----------------------------------------------------------+
| *headers*     | *Optional* | *Array \| Null*    | - Specifies additional headers, like From, Cc, and Bcc.   |
|               |            |                    |                                                           |
|               |            |                    | - Options:                                                |
|               |            |                    |                                                           |
|               |            |                    |   - **From Name**                                         |
|               |            |                    |                                                           |
|               |            |                    |     - Parameter: *from_name*                              |
|               |            |                    |                                                           |
|               |            |                    |     - Required: *Optional*                                |
|               |            |                    |                                                           |
|               |            |                    |     - Type: *String*                                      |
|               |            |                    |                                                           |
|               |            |                    |     - Desc: The display name, also known as the email     |
|               |            |                    |       Sender name.                                        |
|               |            |                    |                                                           |
|               |            |                    |   - **From Email**                                        |
|               |            |                    |                                                           |
|               |            |                    |     - Parameter: *from_email*                             |
|               |            |                    |                                                           |
|               |            |                    |     - Required: *Optional*                                |
|               |            |                    |                                                           |
|               |            |                    |     - Type: *String*                                      |
|               |            |                    |                                                           |
|               |            |                    |     - Desc: Email address of the sender.                  |
|               |            |                    |                                                           |
|               |            |                    |   - **CC**                                                |
|               |            |                    |                                                           |
|               |            |                    |     - Parameter: *cc*                                     |
|               |            |                    |                                                           |
|               |            |                    |     - Required: *Optional*                                |
|               |            |                    |                                                           |
|               |            |                    |     - Type: *String \| Array*                             |
|               |            |                    |                                                           |
|               |            |                    |     - Desc: allows the sender to send a "carbon copy".    |
|               |            |                    |                                                           |
|               |            |                    |     - Example:                                            |
|               |            |                    |                                                           |
|               |            |                    |       - `"user@example.com"`                              |
|               |            |                    |                                                           |
|               |            |                    |       - `"user@example.com, anotheruser@example.com"`     |
|               |            |                    |                                                           |
|               |            |                    |       - `["user@example.com", "anotheruser@example.com"]` |
|               |            |                    |                                                           |
|               |            |                    |   - **BCC**                                               |
|               |            |                    |                                                           |
|               |            |                    |     - Parameter: *bcc*                                    |
|               |            |                    |                                                           |
|               |            |                    |     - Required: *Optional*                                |
|               |            |                    |                                                           |
|               |            |                    |     - Type: *String \| Array*                             |
|               |            |                    |                                                           |
|               |            |                    |     - Desc: allows the sender to send a "Blind carbon     |
|               |            |                    |       copy".                                              |
|               |            |                    |                                                           |
|               |            |                    |     - Example:                                            |
|               |            |                    |                                                           |
|               |            |                    |       - `"user@example.com"`                              |
|               |            |                    |                                                           |
|               |            |                    |       - `"user@example.com, anotheruser@example.com"`     |
|               |            |                    |                                                           |
|               |            |                    |       - `["user@example.com", "anotheruser@example.com"]` |
|               |            |                    |                                                           |
|               |            |                    | - Example:                                                |
|               |            |                    |                                                           |
|               |            |                    |   - `$headers = [`\                                       |
|               |            |                    |     `'from_name' => 'Dailyhunt',`\                        |
|               |            |                    |     `'from_email' => 'do-not-reply@example.in',`\         |
|               |            |                    |     `'cc' => 'user@example.com',`\                        |
|               |            |                    |     `'bcc' => 'anotheruser@example.com'`\                 |
|               |            |                    |     `];`                                                  |
|               |            |                    |                                                           |
|               |            |                    | **Note:** CC & BCC does support multiple email ids.       |
|               |            |                    | Please read the above-mentioned points carefully.         |
+---------------+------------+--------------------+-----------------------------------------------------------+
| *attachments* | *Optional* | *Array \| Null*    | - Specifies attachments parameter.                        |
|               |            |                    |                                                           |
|               |            |                    | - Options:                                                |
|               |            |                    |                                                           |
|               |            |                    |   - **File Name**                                         |
|               |            |                    |                                                           |
|               |            |                    |     - Parameter: *fileName*                               |
|               |            |                    |                                                           |
|               |            |                    |     - Required: *Yes*                                     |
|               |            |                    |                                                           |
|               |            |                    |     - Type: *String*                                      |
|               |            |                    |                                                           |
|               |            |                    |     - Desc: Name of the file.                             |
|               |            |                    |                                                           |
|               |            |                    |   - **File Content**                                      |
|               |            |                    |                                                           |
|               |            |                    |     - Parameter: *fileContente*                           |
|               |            |                    |                                                           |
|               |            |                    |     - Required: *Yes*                                     |
|               |            |                    |                                                           |
|               |            |                    |     - Type: *String*                                      |
|               |            |                    |                                                           |
|               |            |                    |     - Desc: String containing a base64 representation of  |
|               |            |                    |       the source string.                                  |
|               |            |                    |                                                           |
|               |            |                    | - Example:                                                |
|               |            |                    |                                                           |
|               |            |                    |   - `$attachments[] = [`\                                 |
|               |            |                    |     `'fileName' => 'Report.csv',`\                        |
|               |            |                    |     `'fileContent' => base64_encode($content)`\           |
|               |            |                    |     `];`                                                  |
|               |            |                    |                                                           |
|               |            |                    | - **Note**: The attachment parameter should be a          |
|               |            |                    |   multidimensional array.                                 |
+---------------+------------+--------------------+-----------------------------------------------------------+
