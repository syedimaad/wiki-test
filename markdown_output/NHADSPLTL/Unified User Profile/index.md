To identify users across all apps DH/JOSH/MENA/PV as the same user. This
can be done using clientId, gaid incase of android and idfa incase of
ios devices.

**commonDH** cookie → This cookie is present across all apps.

Current commonDH format (decrypted)json{ \"city\": \"bengaluru\",
\"state\": \"karnataka\", \"country\": \"india\", \"countryCode\":
\"IN\", \"source\": \"LOCATION_IP_MODEL\", \"cityId\": \"c17_407\",
\"stateId\": \"s17\", \"locality\": \"bangalore\", \"localityId\":
\"102030819\", \"confidence\": 0.5, \"constituency\": \"mahadevapura\",
\"constituencyId\": \"CN2074_S17\", \"cid\": \"12345679\",
\"last_updated_ts\": 1672895343, \"updated_by\": \"AdEngine\" }

Proposed commonDH format (V1)

Proposed commonDH format top cities added (decrypted)json{ \"city\":
\"bengaluru\", \"state\": \"karnataka\", \"country\": \"india\",
\"countryCode\": \"IN\", \"source\": \"LOCATION_IP_MODEL\", \"cityId\":
\"c17_407\", \"stateId\": \"s17\", \"locality\": \"bangalore\",
\"localityId\": \"102030819\", \"confidence\": 0.5, \"constituency\":
\"mahadevapura\", \"constituencyId\": \"CN2074_S17\", \"cid\":
\"12345679\", \"last_updated_ts\": 1672895343, \"updated_by\":
\"AdEngine\", \"top_cities\": \"{\\\"tci\\\": \[{\\\"c\\\":
\\\"india\\\", \\\"st\\\": \\\"bihar\\\", \\\"ci\\\": \\\"sitamarhi\\\",
\\\"sc\\\": 558.0, \\\"src\\\": \[{\\\"src\\\":
\\\"LOCATION_IP_MODEL\\\", \\\"sc\\\": 558.0}\]}, {\\\"c\\\":
\\\"india\\\", \\\"st\\\": \\\"himachal pradesh\\\", \\\"ci\\\":
\\\"una\\\", \\\"sc\\\": 502.0, \\\"src\\\": \[{\\\"src\\\":
\\\"GPS\\\", \\\"sc\\\": 342.0}, {\\\"src\\\": \\\"CELL\\\", \\\"sc\\\":
160.0}\]}, {\\\"c\\\": \\\"india\\\", \\\"st\\\": \\\"west bengal\\\",
\\\"ci\\\": \\\"nadia\\\", \\\"sc\\\": 486.0, \\\"src\\\":
\[{\\\"src\\\": \\\"GPS\\\", \\\"sc\\\": 270.0}, {\\\"src\\\":
\\\"CELL\\\", \\\"sc\\\": 216.0}\]}, {\\\"c\\\": \\\"india\\\",
\\\"st\\\": \\\"punjab\\\", \\\"ci\\\": \\\"rupnagar\\\", \\\"sc\\\":
336.0, \\\"src\\\": \[{\\\"src\\\": \\\"GPS\\\", \\\"sc\\\": 288.0},
{\\\"src\\\": \\\"CELL\\\", \\\"sc\\\": 48.0}\]}, {\\\"c\\\":
\\\"india\\\", \\\"st\\\": \\\"punjab\\\", \\\"ci\\\":
\\\"hoshiarpur\\\", \\\"sc\\\": 75.6, \\\"src\\\": \[{\\\"src\\\":
\\\"GPS\\\", \\\"sc\\\": 54.0}, {\\\"src\\\": \\\"CELL\\\", \\\"sc\\\":
21.6}\]}\], \\\"u\\\": \\\"2023-01-04T13:55:06+05:30\\\"}\" }

Proposed commonDH format (V2)

Proposed commonDH format (V2). Details in notes{ \"city\":
\"bengaluru\", \"state\": \"karnataka\", \"country\": \"india\",
\"countryCode\": \"IN\", \"source\": \"LOCATION_IP_MODEL\", \"cityId\":
\"c17_407\", \"stateId\": \"s17\", \"locality\": \"bangalore\",
\"localityId\": \"102030819\", \"confidence\": 0.5, \"constituency\":
\"mahadevapura\", \"constituencyId\": \"CN2074_S17\", \"cid\":
\"12345679\", \"last_updated_ts\": 1672895343, \"updated_by\":
\"AdEngine\", \"top_cities\":
\"{\\\"tci\\\":\[{\\\"sc\\\":558,\\\"c_id\\\":\\\"IN\\\",\\\"st_id\\\":\\\"ST_1\\\",\\\"ci_id\\\":\\\"CI_1\\\"},{\\\"sc\\\":502,\\\"c_id\\\":\\\"IN\\\",\\\"st_id\\\":\\\"ST_2\\\",\\\"ci_id\\\":\\\"CI_2\\\"}\],\\\"u\\\":\\\"2023-01-04T13:55:06+05:30\\\"}\",
\"demographics\": \"{\\\"age\\\": 36, \\\"gender\\\": \\\"M\\\",
\\\"l\\\": \\\"2023-01-21T09:20:27.157561+05:30\\\"}\" }

- Added demographics. Age from redis should be first element in array
  and age_range to be excluded.

- Location name to Id changes applicable for JOSH only.

- Limiting top_cities length to top 2 cities in decreasing order of
  score.

- Remove src from sub elements under top_cities.

Sample encrypted commonDH cookienote

%7B%22l%22%3A%7B%22v%22%3A%22iiTIzKCpuKp3L0ALNB77sg9AvBgsNm28GTH4hJamPfFCIpjYx7bGPhlb0HDL4CZX1ylX8llcXnr8lxfl0Gmw7Vv%5C%2Fow0%5C%2FxqrOzhlXUcxhKOJqll4aAnh6qjoe0HjhJDLKmYmXSAJPWzB0fYvdBMy8SbrAQ5%5C%2FLtU5I5MPBphM0JzZuk5LlfKgwbGHrxsoaHk6bKcqmzKE093zawspHpsIQNdKNenNL0gxTF%5C%2F8dQ6xZGY71YVLgFEG2Xpwo1NAvPdUw8Pf%5C%2FSNScBTuSrgdEfrFlyoUV78rIi%2BYJjBsS5BmVCnYW3OJJTqGPo6hxlG%5C%2Fhdc7cNpm9f5OP4IN5csERXyKoFrlzY9q0ksvCM5DHms79DH9D80uo397Jai%5C%2FGtP5JlWFLDBqkZZuxoBUvoCHQ6kpHCm3kwd0xzOHQZbTQJu2pkx1gfu%5C%2Fzab3Znrne3wgihSut5YcUSL4jBzub0UUOp2JciqZNcX2YnjUPmBCMjpmW2asCbELotwRs8%5C%2F6AVe4VzqmR3Zzq%2BH9wm5lIzsDxSe6rp%2B1AIEL6bx3vNr0pkX4Kih9oyCbMJlcLPTyE%2B32XbhTbNsezmWkAZVRepugg5R8p%5C%2Fac2DEUICpdBX5XxcRPZOTUpxB699WxZu5YvAOm8ffyOgpmNQkMeo2PwdP5fSiDJzs%5C%2FnpSlFGh8nAOsqc8wPvJPgRIKqPxZJohY2r56A2rEjV0wB1QJvErI%2BWIJY11yIXLLBvSf8%2BO4nrI31PMgSvnKyj0npPmMZwLIweeerVhlPpxuHJgZjMe%5C%2FCmeHH4QgBixepNcA15TOd8tpHsXpJEw89gCuy8W%2BNgWBdYGLhN02ctaEzUpcaGA0cnUpMUOfjSV%5C%2Fo%2BDJWmaMw5dOEGDykPRApJXwV1ecqvizRuBacF5M7kyr8yq3k1Z70yVKx2T%5C%2FF5Q6Ec%5C%2FISbb8ZRxV3juKsbs89jDeZLPaxoR2h1P66AhHChAcyYC7PzWgYFbzrlQkTgeGIKxyZ5xeL2vzxGZONlggCy2C%2BU7smPZtwHvVHfHmezLkq%5C%2Fwq2SG7VFvjtsAxC5lKjgyuu0UBlF923XcQzbAzpgxVQzsOeD6QvEba3oorG7KKrC%2ByyLp7ub5zs2R3Y0ffKF4pNAcuFU%2B%5C%2FYpCsLEj1quSVatkJf3lExTzkxC7wQ2eH0gsQZyNTGYZzF1IAtqUSPcvxGwu6kKUwpIGV2dWwbtcAjQBMMh8%5C%2F5e751MAy%5C%2FQ1LTObjaCQSXQoO29efFcw%3D%3D%22%2C%22ts%22%3A1674540598%7D%7D

:::: {.panel .conf-macro .output-block style="background-color: rgb(234,230,255);border-color: rgb(153,141,217);border-width: 1.0px;"}
::: {.panelContent style="background-color: rgb(234,230,255);"}
%7B%22l%22%3A%7B%22v%22%3A%22iiTIzKCpuKp3L0ALNB77sg9AvBgsNm28GTH4hJamPfFCIpjYx7bGPhlb0HDL4CZX1ylX8llcXnr8lxfl0Gmw7Vv%5C%2Fow0%5C%2FxqrOzhlXUcxhKOJqll4aAnh6qjoe0HjhJDLKmYmXSAJPWzB0fYvdBMy8SbrAQ5%5C%2FLtU5I5MPBphM0JzZuk5LlfKgwbGHrxsoaHk6bKcqmzKE093zawspHpsIQNdKNenNL0gxTF%5C%2F8dQ6xZGY71YVLgFEG2Xpwo1NAvPdUw8Pf%5C%2FSNScBTuSrgdEfrFlyoUV78rIi%2BYJjBsS5BmVCnYW3OJJTqGPo6hxlG%5C%2Fhdc7cNpm9f5OP4IN5csERXyKoFrlzY9q0ksvCM5DHms79DH9D80uo397Jai%5C%2FGtP5JlWFLDBqkZZuxoBUvoCHQ6kpHCm3kwd0xzOHQZbTQJu2pkx1gfu%5C%2Fzab3Znrne3wgihSut5YcUSL4jBzub0UUOp2JciqZNcX2YnjUPmBCMjpmW2asCbELotwRs8%5C%2F6AVe4VzqmR3Zzq%2BH9wm5lIzsDxSe6rp%2B1AIEL6bx3vNr0pkX4Kih9oyCbMJlcLPTyE%2B32XbhTbNsezmWkAZVRepugg5R8p%5C%2Fac2DEUICpdBX5XxcRPZOTUpxB699WxZu5YvAOm8ffyOgpmNQkMeo2PwdP5fSiDJzs%5C%2FnpSlFGh8nAOsqc8wPvJPgRIKqPxZJohY2r56A2rEjV0wB1QJvErI%2BWIJY11yIXLLBvSf8%2BO4nrI31PMgSvnKyj0npPmMZwLIweeerVhlPpxuHJgZjMe%5C%2FCmeHH4QgBixepNcA15TOd8tpHsXpJEw89gCuy8W%2BNgWBdYGLhN02ctaEzUpcaGA0cnUpMUOfjSV%5C%2Fo%2BDJWmaMw5dOEGDykPRApJXwV1ecqvizRuBacF5M7kyr8yq3k1Z70yVKx2T%5C%2FF5Q6Ec%5C%2FISbb8ZRxV3juKsbs89jDeZLPaxoR2h1P66AhHChAcyYC7PzWgYFbzrlQkTgeGIKxyZ5xeL2vzxGZONlggCy2C%2BU7smPZtwHvVHfHmezLkq%5C%2Fwq2SG7VFvjtsAxC5lKjgyuu0UBlF923XcQzbAzpgxVQzsOeD6QvEba3oorG7KKrC%2ByyLp7ub5zs2R3Y0ffKF4pNAcuFU%2B%5C%2FYpCsLEj1quSVatkJf3lExTzkxC7wQ2eH0gsQZyNTGYZzF1IAtqUSPcvxGwu6kKUwpIGV2dWwbtcAjQBMMh8%5C%2F5e751MAy%5C%2FQ1LTObjaCQSXQoO29efFcw%3D%3D%22%2C%22ts%22%3A1674540598%7D%7D
:::
::::

------------------------------------------------------------------------

MOM: 24-Jan-2023

Details: NHADSPLTL-6546e55da6ef-1840-3475-9293-310ba48d502dSystem JIRA

**Pending:** Confirmation on changes for individual apps to be taken up
or not. **Example**: Specific set of cookies params for each app.
