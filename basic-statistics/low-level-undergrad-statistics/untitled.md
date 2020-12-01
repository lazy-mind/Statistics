# Basic Theories

* Total Probability Theorem
  * $$\begin{aligned} \mathbf{P}(B)=& \mathbf{P}\left(A_{1}\right) \mathbf{P}\left(B \mid A_{1}\right) \\ &+\mathbf{P}\left(A_{2}\right) \mathbf{P}\left(B \mid A_{2}\right) \\ &+\mathbf{P}\left(A_{3}\right) \mathbf{P}\left(B \mid A_{3}\right) \end{aligned}$$ 
  * Decompose an event into MECE sets
* Bayes Theorem
  * $$\begin{aligned} \mathrm{P}\left(A_{i} \mid B\right) &=\frac{\mathrm{P}\left(A_{i} \cap B\right)}{\mathrm{P}(B)} \\ &=\frac{\mathrm{P}\left(A_{i}\right) \mathrm{P}\left(B \mid A_{i}\right)}{\mathrm{P}(B)} \\ &=\frac{\mathrm{P}\left(A_{i}\right) \mathrm{P}\left(B \mid A_{i}\right)}{\sum_{j} \mathbf{P}\left(A_{j}\right) \mathrm{P}\left(B \mid A_{j}\right)} \end{aligned}$$ 
  * Consider $$A_i $$ as a channel, we are looking for MECE channels that can leads to B, and see how much probability that will be $$A_i $$ 
* Independent
  * $$\mathbf{P}\left(A_{i} \cap A_{j} \cap \cdots \cap A_{q}\right)=\mathbf{P}\left(A_{i}\right) \mathbf{P}\left(A_{j}\right) \cdots \mathbf{P}\left(A_{q}\right)$$ 
  * Provides no extra evidence / informatio of other events

