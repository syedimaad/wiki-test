+-----------------------------------+-----------------------------------+
| **What is Network SDK?**          | Network SDK is our in-house SDK   |
|                                   | used for network-related things.  |
|                                   | It is build on Okhttp and solve   |
|                                   | purposes like using same thread   |
|                                   | executor for image and apis call. |
|                                   | Provide connection speed,         |
|                                   | bandwitdth related information    |
+-----------------------------------+-----------------------------------+
| **Why there is a need for same    | Having same thread pool allows us |
| thread pool for api and image?**  | to priortize apis call over       |
|                                   | images                            |
+-----------------------------------+-----------------------------------+
| **What is Analytics SDK?**        | Analytics SDK is our in house SDK |
|                                   | used for batching the events,     |
|                                   | persisting it to the DB and then  |
|                                   | sending it to the URL endpoints   |
|                                   | based on event sections           |
+-----------------------------------+-----------------------------------+
| **What are levels in cards?**     | Each card can have card as a      |
|                                   | child. Same card (id) can come in |
|                                   | Foryou, moreStorie,               |
|                                   | RelatedStories etc. So we         |
|                                   | distinguish each of this with a   |
|                                   | level. Top Level is the the feed  |
|                                   | cards that user sees. It is part  |
|                                   | of primary key of Card table.     |
|                                   | Within each fetch_id, there can   |
|                                   | be same cards at different        |
|                                   | levels.                           |
+-----------------------------------+-----------------------------------+
| **What is local card?**           | It is a card that client insert   |
|                                   | immediately after user submits a  |
|                                   | post (create post flow). After    |
|                                   | create-post API succeeds (which   |
|                                   | may take a while if there are     |
|                                   | multimedia attachments), this     |
|                                   | local cards gets replaced with    |
|                                   | the server returned card. It is   |
|                                   | supposed to show in Foryou and    |
|                                   | Profile \> Myposts                |
+-----------------------------------+-----------------------------------+
| **Why HTTP was used previously    | Previously, we were handling the  |
| and now required to move to       | encrypted data from our end and   |
| HTTPs?**                          | hence wasn\'t relying on HTTPs    |
|                                   | for the same. But due to          |
|                                   | google\'s intervention (Play      |
|                                   | store doesn\'t approve            |
|                                   | application as we have mention in |
|                                   | privacy policy that we will be    |
|                                   | taking some user\'s data and was  |
|                                   | passing on HTTP even though it    |
|                                   | was encrypted)                    |
+-----------------------------------+-----------------------------------+
| **Why do we use SP instead of     | We have setting to increase       |
| DP?**                             | decrease font size within the     |
|                                   | app.                              |
|                                   |                                   |
|                                   | Do not want system setting to     |
|                                   | impact the app text size          |
+-----------------------------------+-----------------------------------+
