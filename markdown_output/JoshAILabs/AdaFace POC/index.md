#### **[ADA FACE]{.underline}**

Paper :
[[[https://arxiv.org/abs/2204.00964]{.underline}]{style="color: rgb(17,85,204);"}](https://arxiv.org/abs/2204.00964)

- Ada face focuses on adaptive marginal loss functions based on quality
  of an image

- The quality assessment is done using the BRISQUE algorithm

- It came out as SOTA for low quality challenging datasets like
  IJB-B,IJB-C and IJB-S datasets

**Base Model :** Inception ResnetV1 (loaded with vggface2 weights)

#### **[Evaluation-1]{.underline}**

Task : Clustered the embeddings of ground truth images of a sample 50
celebrities

Result : Properly separated and tight clusters are formed

#### **[Evaluation-2]{.underline}**

**Scann :** Created a scann based model of adaface ground truth
embeddings And predicted top 10 celebs for particular face and finalized
the best celeb out of these top 10 using finalized strategy based on POC
results.

This Experiment was on done on 100 random items/videos

Generated all best possible zones for all 100 items using above scann
model

For Example,

- Item-1 : detected celebs \["mahesh babu","allu arjun"\]

- Item-2 : detected celebs \["kajal","keerthi suresh"\]

Created a streamlit app to manually tag whether a detected celebrity of
particular item is present in the video or not.

*Results after manual tagging:*

Total : 390

[True positives : 95.75%]{style="color: rgb(56,118,29);"}

[False Positives : 4.25%]{style="color: rgb(255,0,0);"}

***Previous Model used on prod(Inception Resnet):***

Here also, the best celebs are detected for the same items using
Inception ResnetV1

Here also manual tagging is done, to check whether the detected celeb is
present in the video or not

*Results after manual tagging:*

Total : 390

[True positives : 78.25%]{style="color: rgb(106,168,79);"}

[False Positives : 21.75%]{style="color: rgb(255,0,0);"}

#### **[More observations btw 2 models]{.underline}**

**28 cases observed of this type:**

When a celebrity detected by adaface model and has a TRUE label upon
manual tagging ,but Inception ResnetV1 was not able to detect this
celebrity for that item (Basically found 28 False Negatives of Inception
ResnetV1)

**0 cases observed of this type:**

When a celebrity detected by Inception ResnetV1 and has a TRUE label
upon manual tagging ,but adaface model was not able to detect this
celebrity for that item (Basically found zero False Negatives of adaface
model)

#### **[CONCLUSION]{.underline}**

adaface model is better because

- False positives are less compared to Inception ResnetV1

- Ada face is not missing out any true positives detected by Inception
  ResnetV1

- Increase in true positives in adaface case which are not detected by
  Inception ResnetV1
