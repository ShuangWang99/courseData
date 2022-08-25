# DataSet

The data/log_data.json is based on student responses from four classes over a semester in a course called "**Modern Educational Technology and Applications**".When a user answers a problem for multiple times, only the first time is kept. The logs are organized in the structure:

- log_data.json = [user1, user2, ...]
- user = {"user_id": user_id, "log_num": log_num, "logs": [log1, log2, ...]]}
- log = {"exer_id": exer_id, "score": score, "knowledge_code": [knowledge_code1, knowledge_code1, ...]}

The ids/codes are recoded starting from 1.

## Details

```xml
# Number of Students, Number of Exercises, Number of Knowledge Concepts
176,79,5
```