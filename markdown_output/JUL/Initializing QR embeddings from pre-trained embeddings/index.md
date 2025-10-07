# QR embedding

import math class QREmbedding(nn.Module): \"\"\" QR trick from
ByteDance: https://arxiv.org/abs/2209.07663 \"\"\" def
\_\_init\_\_(self, num_embeddings: int, emb_dim: int, sparse: bool =
False): super().\_\_init\_\_() self.\_div =
int(math.sqrt(num_embeddings)) self.\_num_embeddings = self.\_div \*
self.\_div self.\_emb_dim = emb_dim self.\_emb_q =
nn.Embedding(self.\_div, self.\_emb_dim, sparse=sparse) self.\_emb_r =
nn.Embedding(self.\_div, self.\_emb_dim, sparse=sparse) def
forward(self, x: torch.Tensor) -\> torch.Tensor: x = torch.remainder(x,
self.\_num_embeddings) q = torch.div(x, self.\_div,
rounding_mode=\"floor\").long() r = torch.remainder(x,
self.\_div).long() return self.\_emb_q(q) + self.\_emb_r(r)

# Question: Can we learn useful pairwise-geometries using the QR trick?

Use BLIP embeddings and learn pairwise geometry of the video_ids using
QR embedding (10x compression) like so of the hashed ids (`hashed_idx`
in code)

batch_size = 2 \*\* 10 num_epochs = 50 temperature_fn = lambda epoch:
max(0.5 \* (0.95 \*\* epoch), 0.05) num_batches = hashed_idx.shape\[0\]
// batch_size idx_true = np.arange(0, hashed_idx.shape\[0\]) optim =
torch.optim.Adagrad(model.parameters(), lr=5e-1) criterion =
nn.KLDivLoss(reduction=\"batchmean\", log_target=True) pairwise_distance
= PairwiseDistance() for epoch in range(num_epochs): idx_reordered =
np.array(idx_true) np.random.shuffle(idx_reordered) temperature =
temperature_fn(epoch) for batch_nb in range(num_batches): idx_this =
idx_reordered\[(batch_nb \* batch_size): ((batch_nb + 1) \*
batch_size)\] hashed_idx_this = hashed_idx\[idx_this\].long()
actuals_this = actuals_normed\[idx_this\] optim.zero_grad() emb_val =
F.normalize(model(hashed_idx_this), p=2.0, dim=1) batch_size =
emb_val.size(0) pred = emb_val.matmul(emb_val.transpose(0, 1)) pred =
torch.where(torch.eye(batch_size) \> 0, -1000 \* torch.ones_like(pred),
pred) pred = F.log_softmax(pred / temperature, dim=1) target =
actuals_this.matmul(actuals_this.transpose(0, 1)) target =
torch.where(torch.eye(batch_size) \> 0, -1000 \*
torch.ones_like(target), target) target = F.log_softmax(target /
temperature, dim=1) loss = criterion(pred, target) loss.backward()
optim.step()

# Results

ANN results are comparable (recall @ 100 is approximately 65%)
