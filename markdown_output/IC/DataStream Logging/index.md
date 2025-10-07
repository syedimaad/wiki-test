# Overhead Bytes

Overhead Bytes = Request TCP Overhead + Request IP Overhead + Request
ETH Overhead + Response TCP Overhead + Response IP Overhead + Response
ETH OverheadProtocolOverheadBytes =  HTTP headers +  UDP/TCP Overhead +
IP Overhead + ETH Overhead.Total Bytes =  ContentResponseBytes +
ProtocolOverheadBytes + RequestBodyBytesBytes = ContentResponseBytes
\[HTTP/1.1\] Bytes = ContentResponseBytes + Overhead Bytes \[in case of
HTTP/2\] Bytes = ContentResponseBytes + Overhead Bytes + Quic Overheader
\[in case of HTTP/3\]
