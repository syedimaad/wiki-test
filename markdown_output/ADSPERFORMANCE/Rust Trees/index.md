In production rust_trees, we have a function for each node of a tree
(eg. `tree_3_node_5()`), and the tree traversal is done by starting with
node 0 and calling a chain of functions till we reach leaf.

These functions form around 10k lines of code for each rust model,
leading to a slow compilation. The idea of this project is to improve
compilation time (by reducing code) and still maintain similar
prediction time and memory/CPU usage at run-time.

**Approaches tried out to store JSON data in rust model:**

1.  Tree is stored as `HashMap<i32, Box<dyn Node>>`, where `Node` is
    implemented by `InnerNode` and `LeafNode`. A `Vec<Tree>` forms the
    structure for storing JSON data.

    1.  This approach took 155 min to compile by including 457 models in
        `rust_trees`. With one model, it took only over a minute to
        compile, so this does not seem to scale.

2.  Tree is stored as `HashMap<i32, Node>`, where `Node` is a struct
    formed by combining the fields of both `InnerNode` and `LeafNode` as
    defined in approach 1.

    1.  This reduced the compilation time to 50 minutes.

3.  Tree is `Vec<Node>`. We can replace `HashMap` by a `Vec` because the
    `node_id`s stored in the above approaches were continuous. And `Vec`
    indexing is faster than `HashMap` access, so this is an overall
    better structure.

    1.  While this approach is expected to run faster, it took more time
        to compile (69 minutes).

4.  Removed `lazy_static`. Instead, declared a static array of trees in
    the following manner. It reduced the compilation-time to **2.5
    minutes** (i.e. **10x** less than the current prod binary
    compile-time).

pub static TREES: &\'static \[&\'static \[Node\]\] = &\[ &\[Node { id:
1, feature: 102, condition: 1.5, missing: 2, yes: 3, no: 2, is_leaf:
false, leaf: 0.0, } \]\];

The above approach (#4) has CPU usage (computed on test MIG using RPS of
1.5x the prod, i.e. 4500 RPS, and giving 15 minutes each for prod and
new binary), similar to current prod binary = 82%.

Memory usage is also expected to be the same since there is no
additional caching requirement. The compile-time static maps are stored
within the binary itself.

Hence, this was deployed. \[[Merge
Request](https://gitlab.dailyhunt.in/nh-ads-platform/AdLearning/merge_requests/178)\]
