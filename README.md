# review_opinion-dynamics

## implementing the model with the update function: --- done <br>
$𝑥_𝑖(t+1) = 𝑥_𝑖 + \dfrac{𝛽_𝑖}{∑_{𝑗≠𝑖} 𝑤_{𝑖𝑗}}  ∑_{𝑗≠𝑖} 𝑤_{𝑖𝑗}   𝑥_{𝑖𝑗} ∙ tanh⁡(−𝛼_𝑖 (|𝑥_{𝑖𝑗} | − 𝜌_𝑖))$<br>

𝑥_𝑖 (𝑡),𝑥_𝑗 (𝑡) ∈ [0,1] --> Opinions of individuum 𝑥_𝑖 and its neighbors<br>
𝑥_{𝑖𝑗} (𝑡) = 𝑥_𝑗 (𝑡) - 𝑥_𝑖 (𝑡)  ∈ [-1,1] --> difference of opinion<br>
𝑤_𝑖𝑗 ∈ [0,1] --> social influence parameter (edge weights, allows unsymmetrical influence)<br>
𝛼_𝑖 ∈ [0,+…] --> controversy  of the topic (nonlinearity parameter,)<br>
𝜌_𝑖 ∈ [0,1]--> max opinion difference before repulsion<br>
𝛽_𝑖 --> coupling strength (stubborn agents)<br>



 find issues that fix opinions only growing in value-- fixed <br>
 colorbar is not stable between 0 and 1 --- fixed <br>
 
 ## trying to find a paremeter for polarization/radicalization/consent --- done? <br>
 find parameter for steady state.. <br>
 memory of old opinion list compared to new? if true stop?<br>
 ---> doesnt work... because of converging <br>
 

 polarization/radicalization/consent over mean and varianz of opinion list:<br>

 polarization:?<br>
 varianz opinion list > 𝜌_𝑖 ?<br>
 radicalization:?<br>
 mean opinion list not > 0.5 or <0.5<br>
 varianz opinion list << 𝜌_𝑖<br>
 consent:<br>
 mean opinion list around 0.5 <br>
 varianz opinion list << 𝜌_𝑖 ?<br>

 ## testing out model for different parameters:

 𝑥_𝑖 (𝑡),𝑥_𝑗 (𝑡) ∈ [0,1] --> how heterogen?<br>
𝑤_𝑖𝑗 ∈ [0,1] --> first homogen later how heterogen/asymmetrical (social influence parameter if heterogen)<br>

𝛼_𝑖 ∈ [0,+…] --> homogene, heterogen (controversity)<br>
𝜌_𝑖 ∈ [0,1]--> homogene, heterogen(threshood before repulsion)<br>
𝛽_𝑖 --> homogene, heterogen (coupling strength)<br>

different network struktures:<br>
random net,all to all, grid<br>

 without repulsion cutting function: if $|𝑥_{𝑖𝑗}|>𝜌_{i}\text{-->   }𝑥_𝑖(𝑡+1)=𝑥_𝑖$<br>

 writing down table of what has been calculated with results:<br>


 ## adding a modified update function for complex contagion:
  $𝑥_𝑖(t+1) = 𝑥_𝑖 + \dfrac{𝛽_𝑖}{∑_{𝑗≠𝑖} 𝑤_{𝑖𝑗}}  ∑_{𝑗≠𝑖} 𝑤_{𝑖𝑗}   𝑥_{𝑖𝑗} ∙ tanh⁡(−𝛼_𝑖 (|𝑥_{𝑖𝑗} | − 𝜌_𝑖))$<br>
 shifting the tanhyp before the sum
 $<𝑥_{𝑗n}>  = \dfrac{1}{∑_{𝑗≠𝑖} 𝑤_{𝑖𝑗}}  ∑_{𝑗≠𝑖} 𝑤_{𝑖𝑗}   𝑥_{𝑗} ∙ tanh⁡(−𝛼_𝑖 (|𝑥_{𝑖𝑗} | − 𝜌_𝑖))$<br>
 $𝑥_𝑖(t+1) = 𝑥_𝑖 + 𝛽_𝑖 ∙ tanh( -𝛼_𝑖 (\dfrac{1}{∑_{𝑗≠𝑖} 𝑤_{𝑖𝑗}}  ∑_{𝑗≠𝑖} 𝑤_{𝑖𝑗}   𝑥_{𝑗} -  𝑥_𝑖 ∙ tanh⁡(−𝛼_𝑖 (|𝑥_{𝑖𝑗} | − 𝜌_𝑖))$<br>

 oder?<br>
   $𝑥_𝑖(t+1) = 𝑥_𝑖 + 𝛽_𝑖 ∙tanh⁡(\dfrac{𝛽_𝑖}{∑_{𝑗≠𝑖} 𝑤_{𝑖𝑗}}  ∑_{𝑗≠𝑖} 𝑤_{𝑖𝑗}   𝑥_{𝑖𝑗} ∙ (−𝛼_𝑖 (|𝑥_{𝑖𝑗} | − 𝜌_𝑖)))$<br>
