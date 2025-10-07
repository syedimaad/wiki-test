# REST API

**GET /api/v1/users/{aduid}**

{ \"aduid\": \"{aduid}\", \"demographics\": { \"agerange\": \"25-30\",
\"gender\": \"M\" }, \"top_cities\": { \"cities\": \[ { \"country\":
\"india\", \"state\": \"uttar pradesh\", \"city\": \"lucknow\",
\"score\": 90.0, \"source\": \[ { \"source\": \"IP\", \"score\": 90.0 }
\] } \], \"updated_at\": \"2023-01-02T10:41:18+05:30\" } }

**GET /api/v1/users/{aduid}/location**

{ \"aduid\": \"{aduid}\", \"top_cities\": { \"cities\": \[ {
\"country\": \"india\", \"state\": \"uttar pradesh\", \"city\":
\"lucknow\", \"score\": 90.0, \"source\": \[ { \"source\": \"IP\",
\"score\": 90.0 } \] } \], \"updated_at\": \"2023-01-02T10:41:18+05:30\"
} }

**GET /api/v1/users/{aduid}/demographics**

{ \"aduid\": \"{aduid}\", \"demographics\": { \"agerange\": \"25-30\",
\"gender\": \"M\" } }
