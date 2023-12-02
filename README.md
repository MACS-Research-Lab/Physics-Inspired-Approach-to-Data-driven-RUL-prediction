# Physics-Inspired-Approach-to-Data-driven-RUL-prediction
In engineering prognostics, predicting remaining useful life (RUL) is crucial. Traditional data-driven methods lack flexibility and explanability. Our work introduces a flexible, explainable model inspired by physics approach. It provides adjustable prediction conservatism without retraining the model.


\begin{table*}[t]
          \centering
                \small % text size of table content
                \begin{tabular}{clrrr} % alignment of each column data
                    \toprule[\heavyrulewidth]\toprule[\heavyrulewidth]
                    \textbf{Hyper-param} & \textbf{Description} &\textbf{Range}&\textbf{Direct}&\textbf{Composition} \\ 
                    \midrule
                     $d^p_{\text{emb}}/n^p_{\text{head}}$  & Head dimension self-attention  (Performance block)   &$\{1,2,3,4,\dots,12\}$ & 12 & 4\\
                    $n^p_{\text{head}}$ &  Number of heads of self-attention (Performance block)    &  $\{1,2,3,\dots,12\}$  & 9 &   9 \\
                    $d^p_{\text{feed}}$  & Dimension of feed-forward network(Performance block)      &  $\{16,32, 64,\dots,1024\}$ &  1024&  1024\\
                    $d^p_{\text{MPL}}$ & Wide of the two Layers of MLP network(Performance block)      &  $\{32, 64,128,\dots,1024\}$ & 64&  1024\\
                    $p^p$& Dropout (Performance block)  &  $[0,0.5]$ & 0.267  & 0.235 \\
                        &    &  &  & \\                
                    $d^i_{\text{emb}}/n^i_{\text{head}}$  & Head dimension self-attention  (Future input block)   &$\{1,2,3,4,\dots,12\}$ & 4 & 12\\
                    $n^i_{\text{head}}$ &  Number of heads of self-attention (Future input block)    &  $\{1,2,3,\dots,12\}$  & 1 &    1\\
                    $d^i_{\text{feed}}$  & Dimension of feed-forward network(Future input block)      &  $\{16,32, 64,\dots,1024\}$ & 128  & 32 \\
                    $d^i_{\text{MPL}}$ & Wide of the two Layers of MLP network(Future input block)      &  $\{32, 64,128,\dots,1024\}$ & 256 & 128 \\
                     $d_{\text{enc}}^i$& Future inputs encoding dimension (Future inputs block)  &  $\{1, 2,4,8,12,16\}$ & 1 &12 \\
                    $p^i$& Dropout (Future input block)  &  $[0,0.5]$ & 0.024 &0.38   \\
                   
                         &    &  &  & \\   
                    $d_{\text{RUL}}$  & Wide of the two layers of MLP network for RUL prediction  &  $\{32, 64,128,\dots,1024\}$ & $1024$ & $128$ \\
                    $lr^{p}$ & Learning rate(Performance block)  &  $[10^{-5},10^{-3}]$ &  &  $3.1\cdot 10^{-5}$   \\
                    $lr^{i}$ & Learning rate(Future inputs block)  &  $[10^{-5},10^{-3}]$ & $4\cdot 10^{-5}$ &  $8.6\cdot 10^{-4}$   \\
                    $n^p_{\text{Epoch}}$ & Number of Epochs (Performance block) &  $\{15,16,17,\cdots,30\}$ &  & $30$\\
                    $n^i_{\text{Epoch}}$ & Number of Epochs (Future inputs block) &  $\{15,16,17,\cdots,30\}$ &$50^*$  & $20$\\
                    \midrule
                    \bottomrule[\heavyrulewidth] 
                \end{tabular}
                \caption{Hyper-parameters of composition and direct prediction models. The range of the number of epochs of the direct prediction model was $\{15,16,17,\cdots,50\}$  } 
                \label{tab: Hyperparameters}               
                %\footnotesize{\textit{* degradation parameter}}
        \end{table*}%
