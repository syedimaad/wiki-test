PUBLISHEDGreen

1.  APIs are annotated with `Cl-apiStatsCapture` header to indicate to
    `HeaderInterceptor` to track this request. ` HI` then

    1.  delegates to `ApiPerHelper` which adds this req-Id to its queue

        1.  on getting response ApiPerHelper checks if this request-id
            is already present in the map, it calculates RTT params;
            else not

    2.  removes header and forwards req

2.  Many things are feed calls, we only want to track the ones that end
    up in SLV, so `FPUsecase` and `NPUsecase` will add the header.
    Others do not

3.  Detail page (for SPV) and entity-page (feed is piggy-backed to it)
    APIs also pass the header

4.  At different points of instrumentation, we look up in
    `ApiPerfHelper` to add the params

5.  x-request-id from (header extracted from ) response is copied to
    `ApiResponse<>` and serviceimpls copy it to further down (to each
    and every item recursively)

    1.  For feed this is done in ApiResponseOperator

    2.  In other places, it is done by parsing `Response<T>` and calling
        this function explicitly.
