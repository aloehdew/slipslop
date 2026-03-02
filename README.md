## Inspiration
1-Dimensional Convolutional Neural Networks (1dCNNs) are incredibly powerful tools for the study of nucleotide sequences. In searching for applications, we could find none that had been developed for the specified purpose of detecting Programmed Ribosomal Frameshifting (PRF), an important translation phenomenon in the understanding of virology.
## What it does
- SlipSlop takes a 250bp nucleotide sequence and returns the probability that the sequence contains a PRF site 
- Particularly accurate for -1 PRF frameshifts that contain the slippery site heptamer motif.
## How we built it
- After collecting ~1250 known slip-sites from NCBI databases, augmenting data to construct larger training sets, and pulling negative examples, we ended up with ~75,000 data-points that were passed into a convolutional deep neural network for training. 
- Done in Jupyter Notebooks using PyTorch for network construction and Biopython for data collection.
  <img width="1821" height="641" alt="chart1" src="https://github.com/user-attachments/assets/3fabd800-575a-4236-93ab-93dc69e9470f" />
## Challenges we ran into
- When augmenting data, we had to make sure not to introduce any augmentation artifacts that would bias results. 
- Since the majority of existing data comes from just a few viral families, it is hard to properly cluster data for splitting and we relied instead on random splitting. 
- This data is also heavily biased toward -1 frameshift slippage sites, leading that to be the main strength of the model's recognition.
## Accomplishments that we're proud of
<img width="984" height="238" alt="precision" src="https://github.com/user-attachments/assets/c231c89f-5c95-475b-97b9-f133e1c7929d" />

- When testing against the same known viral -1 PRF site sequences, our model outperformed the only other tool for detecting these sites, PRFect. 
- With a Recall of 40% compared to their 8% and precision of 90% compared to their 97%, we argue that our tool has better performance since False Positives are easier to disprove through other tools while False Negatives may lead to a critical omission of translational behavior. 

## What we learned
- First and foremost, we learned a tremendous amount about model design and data curation. 
- Further, we were able to gain a much deeper understanding of _why_ existing tools have the limitation that they do; particularly, that the availability of datasets for niche biological phenomenon are usually not well maintained and often difficult to find or interpret. 
## What's next for SlipSlop
- The model would benefit heavily from longer training and more data, as any neural network would.
- In order to create a viable product we must institute proper data clustering, something that would only be possible if a wider variety of positive data existed. 
- If such data existed, the overall ambition for this tool would be to expand its functionality to detect all forms of PRF, even though they can use diverse and vastly different mechanisms. This would likely involve scaling the depth, width, and resolution of our model.
