**VERDICT: DROPPED / NOT IMPLEMENTED**

**Reason:** Since there is negligible difference between the data sizes
of compressed JSON and Protobuf, combined with the effort and overhead
clients will have to endure to replace json with proto, there is no
benefit in pursuing this path any further.

### Uncompressed

  ---------------------------------------------------------------------------------------------------------------------------- ------------------------- ------------------------------- -----------------
  **API**                                                                                                                      **JSON text size (KB)**   **Protobuf binary size (KB)**   **Reduction %**
  [[For+You]{.underline}](https://drive.google.com/drive/folders/1wEfi6VGnewKy__Wbl_cW8PPTulNGnvmJ?usp=drive_link)             210                       145                             **30.95**
  [[For+You Post body]{.underline}](https://drive.google.com/drive/folders/1KZuWS7ObrDCBT2naLQtn8lIWGb5tSNna?usp=drive_link)   2                         0.26                            **87**
  [[Page Sync]{.underline}](https://drive.google.com/drive/folders/1HqIJUpBzJk_UEMT4We3WDZeit1boFQpU?usp=drive_link)           31                        16                              **48.39**
  [[Bottom Bar]{.underline}](https://drive.google.com/drive/folders/1oYfiDbkdSj8tjx0awxpphEKEUqG_xKhY?usp=drive_link)          28                        17                              **39.29**
  ---------------------------------------------------------------------------------------------------------------------------- ------------------------- ------------------------------- -----------------

### Compressed (Using gzip at compression level 6)

> Gzip has 9 compression levels; 1 to 9. To tabulate the following data,
> all files are compressed at level 6. *[Please note that the compressed
> size remains the same at levels 6 through 9.]{.underline}*

  ---------------------------------------------------------------------------------------------------------------------------- ------------------------- ------------------------------- -----------------
  **API**                                                                                                                      **JSON text size (KB)**   **Protobuf binary size (KB)**   **Reduction %**
  [[For+You]{.underline}](https://drive.google.com/drive/folders/1wEfi6VGnewKy__Wbl_cW8PPTulNGnvmJ?usp=drive_link)             27                        26                              **3.7**
  [[For+You Post body]{.underline}](https://drive.google.com/drive/folders/1KZuWS7ObrDCBT2naLQtn8lIWGb5tSNna?usp=drive_link)   0.7                       0.24                            **65.71**
  [[Page Sync]{.underline}](https://drive.google.com/drive/folders/1HqIJUpBzJk_UEMT4We3WDZeit1boFQpU?usp=drive_link)           4                         3                               **25**
  [[Bottom Bar]{.underline}](https://drive.google.com/drive/folders/1oYfiDbkdSj8tjx0awxpphEKEUqG_xKhY?usp=drive_link)          5                         5                               **0**
  ---------------------------------------------------------------------------------------------------------------------------- ------------------------- ------------------------------- -----------------

note

The difference between the gzipped (level 6, default) JSON and Proto
binaries is quite insignificant. Specially for larger responses, e.g.
For+You: 27KB to 26KB.

*The degree of effort will be much higher than the actual gain.*

**Erratic results:** The size difference is observed to be higher in
smaller JSON responses after compression.

:::: {.panel .conf-macro .output-block style="background-color: rgb(234,230,255);border-color: rgb(153,141,217);border-width: 1.0px;"}
::: {.panelContent style="background-color: rgb(234,230,255);"}
The difference between the gzipped (level 6, default) JSON and Proto
binaries is quite insignificant. Specially for larger responses, e.g.
For+You: 27KB to 26KB.

*The degree of effort will be much higher than the actual gain.*

**Erratic results:** The size difference is observed to be higher in
smaller JSON responses after compression.
:::
::::

### Summary

1.  The above comparison is tabulated by

    1.  Creating a Proto (.proto) schema from existing JSON Responses

    2.  Creating a python module for the given proto schema

    3.  Converting the JSON to proto binary using the python object and
        the proto schema using a python script

2.  The online tools for creating proto schema from JSON have proven to
    be unreliable with bigger, more complicated JSON structures. Some of
    the common issues include:

    1.  **Duplicate nested types:** Tools generate separate types for
        every slight variation instead of unifying them.

    2.  **Incorrect map\<string, any\>:** Tools often misinterpret
        generic dictionaries as full-fledged nested messages or arrays.

    3.  **Flat conversion, no package or semantic grouping:** You lose
        structure and meaningful reuse.

3.  In this exercise, GitHub Copilot is used to create protobuf schemas
    from JSON. Although not perfect, it was more reliable than many
    online tools. Took some hit & trial to add missing properties, fix
    nested schema, fix map notations, etc.

------------------------------------------------------------------------

### Considerations

1.  Proto will add complexity to the development and debugging processes
    for the clients. Difficult to analyze request and response in tools
    like Charles

2.  Syncing overhead, after every change, the `.proto` schema needs to
    be synced among all clients and BE

3.  Considering the redundancy required for models to support both JSON
    and Proto (1 for each), the ideal approach will be to switch
    completely over to Proto for certain APIs. Building interoperability
    between the two will added overhead and can be error prone.

4.  If both JSON and Proto are expected to be supported, extremely
    difficult to use the same Kotlin/Java/Swift model between JSON and
    Proto because of deeply structured and tightly coupled behaviour of
    Protobuf models ***(Confirmed in Swift)***

5.  Considering the redundancy required for models to support both JSON
    and Proto (1 for each), the ideal approach will be to switch
    completely over to Proto for certain APIs

------------------------------------------------------------------------

### JSON to Protobuf Binary Converter

Script file:
[j2pb.py](https://drive.google.com/file/d/1K4fbaCyXDZVLrYpDg0RrKyrUde72c6mG/view?usp=drive_link)

This Python script encodes a JSON input file into a binary `.pb` file
using a provided `.proto` schema. It dynamically compiles the schema and
uses the specified Protobuf message type for encoding.

### Prerequisites

- Python 3.x

- `protobuf` Python package:

  pip install protobuf

- `protoc` compiler must be installed and available in your system\'s
  `PATH`

- A `generated.proto` schema file created from JSON. Can use AI tools or
  any online converter.

### Usage

python j2pb.py \<schema.proto\> \<input.json\> \<MessageType\>
\<output.pb\>

#### Parameters

- `<schema.proto>`: Path to your Protobuf schema file

- `<input.json>`: JSON file with the data to be encoded

- `<MessageType>`: Name of the top-level message to use from the schema
  (e.g. `Root`, `api.User`)

- `<output.pb>`: Destination path for the encoded binary output

### Example

python j2pb.py generated.proto user.json Root user_output.pb

This command will:

1.  Compile `generated.proto` into a Python module

2.  Load and parse the `user.json` file using the `Root` Protobuf
    message

3.  Serialize the message and write the output to `user_output.pb`

### Notes

- The script will attempt to dynamically load the generated `*_pb2.py`
  file from the same directory.

- If your `.proto` file uses a `package`, use the fully qualified
  message name (e.g. `api.Root`).

- The output `.pb` file can be decoded with `protoc --decode` or used
  directly in client applications that share the same schema.
