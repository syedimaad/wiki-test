  ------ ------------------------------ ---------------------------------- ---------------
  Case   Range Header Type              Example Range Header               Response Code
  1      0 \<= start \< end \< length   \"Range: bytes=1000-2000\"         206
  2      start \> end                   \"Range: bytes=2000-1000\"         200
  3      end \> file_size               \"Range: bytes=1000000-6000000\"   206
  4      Alphanumeric chars             \"Range: bytes=asdf1234\"          200
  5      start \>= file_size            \"Range: bytes=6000000-\"          200
  6      "bytes=0-0"                    \"Range: bytes=0-0\"               206
  ------ ------------------------------ ---------------------------------- ---------------
