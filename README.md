# pointer-generator
Code for my final MSc project on pointer-generator networks and transformer networks for abstractive summarisation.

This has 4 models:
1) RNN - model adapted from [the PyTorch documentation](https://pytorch.org/tutorials/intermediate/seq2seq_translation_tutorial.html)
2) RNN with attention - built up on the first model
3) RNN with attention and pointer-generator network - adapted from the original code by the paper author for Get to the Point (<https://github.com/abisee/pointer-generator> and <https://github.com/laihuiyuan/pointer-generator>) 
3) Transformer - Fine-tuned mT5 using Huggingface

###Dataset
For the first two, I've used the CSV files from Kaggle, which you can find here: <https://www.kaggle.com/datasets/gowrishankarp/newspaper-text-summarization-cnn-dailymail>
The third model requires chunked data that you can find here under FINISHED_FILES: <https://github.com/JafferWilson/Process-Data-of-CNN-DailyMail>
For the Transformer model, I've used huggingface, which has the CNN-DM dataset on their datasets API.

##How to run the models
For the first two models and the transformer model, everything should be straightforward - run the cells in the python notebooks.

###Pointer-generator
For the pointer-generator model, as I mentioned, I've adapted and debugged the code from the original paper author above.
Once you've downloaded and unzipped the finished_files, make a log directory in your project folder and update all paths in 
`utils/config.py`.

Clone <https://github.com/andersjo/pyrouge>, which has a ROUGE-1.5.5 directory under tools. 
Run `pip install pyrouge` to install `pyrouge-0.1.3`.
Run `set pyrouge_set_rouge_path=<PATH_TO_ROUGE-1.5.5_FOLDER>`

Finally, to train, run `python train.py`.
This will put the model in your log directory along with other logging information.

To evaluate or test,
run `python test\eval.py <PATH/TO/MODEL>`
