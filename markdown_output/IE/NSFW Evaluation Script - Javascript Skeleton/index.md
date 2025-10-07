### 1. Custom Model: NSFW Detection Post-Processing Script

#### Input

wide760- labels: \[\] or stringified array \[ { label: \"neutral\",
confidence: 0.95 }, { label: \"nsfw\", confidence: 0.05 } \... \]

#### Output

wide760{ isNSFW: boolean, confidence: float (0 to 1), metadata: {} extra
output info, not parse/understood by client. }

### OCR: NSFW Detection Post-Processing Script for keywords

#### Input

wide760- labels: \[\] or stringified array, \[ { label: \"neutral\",
confidence: 0.95 }, { label: \"nsfw\", confidence: 0.05 } \... \], -
title: Title from native ads, - body: description, - langIds: \[\"en\",
\"hi\", \...\]

#### Output

wide760{ isNSFW: boolean, confidence: number (0 to 1), metadata: {}
extra output info, not parse/understood by client. }
