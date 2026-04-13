## From metrics to topologies

The purpose of this post is to provide a dictionary translating between metrics and distance, and topology and open sets. I've written up proofs of two results I see as important, largely as a revision exercise for my upcoming course in topology. The first lets us go between viewing continuity analytically in terms of metrics, and topologically in terms of open sets.

**Theorem 1** Let $(X, d)$ and $(Y, d')$ be a metric spaces, and let $f \colon X \to Y$ be a function. Then, $f$ is continuous if and only if, for every open set $U \subseteq Y$, the set $f^{-1}(U)$ is open in $X$.

*Proof.* $(\Rightarrow)$ Suppose that $f$ is continuous, and let $U \subset Y$ be open. Pick any $x_0 \in f^{-1}(U)$. Since $U$ is open, we can find $\epsilon > 0$ such that the open ball $B_{d'}(f(x_0), \epsilon) \subseteq U$. Plugging this value of $\epsilon$ into our continuity definition for $f$, we find that there exists $\delta > 0$ such that, if $x \in X$ with $d(x, x_0) < \delta$, then $d'(f(x), f(x_0)) < \epsilon$. Therefore, for any $x \in B_d(x_0, \delta)$, we have $f(x) \in B_{d'}(f(x_0, \epsilon) \subseteq U$. It follows that $x \in f^{-1}(U)$, and so, $B_d(x_0, \delta) \subseteq f^{-1}(U)$. Since $x_0$ was arbitrary, $f^{-1}(U)$ is open.

$(\Leftarrow)$ Now suppose that, for any open set $U \subseteq Y$, the set $f^{-1}(U)$ is open in $X$. Let $\epsilon > 0$ be fixed. For any $x_0 \in X$, the open ball $B_{d'}(f(x_0), \epsilon)$ is itself open in $Y$. Therefore, its preimage $f^{-1}(B_{d'}(f(x_0), \epsilon))$ is open in $X$, and so we can find $\delta > 0$ such that $B_{d}(x_0, \delta) \subseteq f^{-1}(B_{d_1}(f(x_0), \epsilon))$. In other words, $f(B_d(x_0, \delta)) \subseteq B_{d'}(f(x_0), \epsilon)$. We conclude that, for any $x \in X$ with $d(x, x_0) < \delta$, we have $d'(f(x), f(x_0)) < \epsilon$. Since $x_0$ and $\epsilon$ were both arbitrary, this means $f$ is continuous. $\blacksquare$

Now we will talk about what it means for two metrics to be equivalent. There are two different ideas here, one from analysis and one using topology. As we will see, one is stronger than the other.

**Defintion.** Let $(X, d)$ and $(X, d')$ be metrics spaces. The metrics $d$ and $d'$ are called *(bilipschitz) equivalent* if there exist constants $0 < c_1 < c_2$ such that

$$ c_1 d'(x, y) \le d(x, y) \le c_2 d'(x, y)$$

for all $x, y \in X$.

**Theorem 2.** If metrics $d$ and $d'$ are equivalent, then they generate the same collection of open sets. That is, any set $U \subseteq X$ is open in $(X, d)$ if and only if it is open in $(X, d')$.

*Proof.* Suppose that $d$ and $d'$ are equivalent. Let $U \subseteq X$ be open with respect to $d$, and pick any $x_0 \in U$. We can find $\epsilon > 0$ such that the open ball $B_d(x_0, \epsilon) \subseteq U$. Using the definiton of equivalence, for any $x \in X$ with $d'(x, x_0) < \epsilon / c_2$, we have

$$ d(x, x_0) \le c_2 d'(x, x_0) < \epsilon.$$

So, if $x \in B_{d'}(x_0, \epsilon / c_2)$, then $x \in B_d(x_0, \epsilon)$. It follows that $B_{d'}(x_0, \epsilon / c_2) \subseteq B_d(x_0, \epsilon) \subseteq U$. Since $x_0$ was arbitrary, we conclude that $U$ is also open with respect to $d'$. Since this situation is symmetric in the metrics $d$ and $d'$, the claim follows. $\blacksquare$

We might ask about the converse of Theorem 2.

**Counterexample.** Consider $\mathbb{Z}$ with $d_1$ the discrete metric, and $d_2$ the euclidean metric inherited from $\mathbb{R}$. Both of these metrics induce the same topology, namely the discrete topology, however they are certainly not equivalent metrics in the analytic sense: $d_1$ is bounded by $1$, and $d_2$ is unbounded.

Unlike the defintion of continuity, our definition of equivalence will not map over perfectly to topological spaces. This becomes a theme when making the jump from metric to topological spaces: many ideas from analysis gain a certain 'fuzziness' when brought over to topology, and we have to choose definitions that aren't quite equivalent. We say that two metrics are *topologically* equivalent if they induce the same collection of open sets, which is a weaker notion that the analytic defintion. Another classic example of this fuzziness is the idea of limits of sequences in topological spaces.
