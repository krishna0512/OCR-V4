## Training, Finetuning and Evaluation:


## Dataset preparation:
- Create LMDB files for train, validation and test dataset splits.
Please follow README under "create_lmdb_dataset" folder 


## Training:

(i) Please create a text file containing characters of a partcular langauge and name it as "bengali_charlist.txt" and kept it in path  "main_code/alphabet/"
(ii) Please check l1 (line 42) and l2 (line 43) in code "lang_train.py" in "main_code" folder whether language name is mentioned or not. If language name is not mentioned then please write the language name.   


##To train model (TPS-ResNet-BiLSTM-CTC) from scratch:

cd main_code

python3 lang_train.py --mode train --lang bengali --trainRoot create_lmdb_dataset/bengali/train_lmdb --workers 5 --valRoot create_lmdb_dataset/bengali/val_lmdb --batchSize 64 --nepoch 50 --cuda --out out --displayInterval 23000 --valInterval 23000  --adadelta

--trainRoot is training dataset path containing train_lmdb 
--valRoot is validation dataset path containing val_lmdb
--nepoch is number of epoch (for training)
--out is output folder containing trainined model (model saved according to best CRR and WRR)

(i) Please see config.py file, if you want to change these parameters

##To Finetune the already trained model: 

cd main_code

python3 lang_train.py --mode train --lang bengali --trainRoot create_lmdb_dataset/bengali/train_lmdb --workers 5 --valRoot create_lmdb_dataset/bengali/val_lmdb --pretrained  out/crnn_results/best_cer.pth --batchSize 64 --nepoch 50 --cuda --out out 
--displayInterval 23000 --valInterval 23000  --adadelta

--pretrained is trained model path containing pretrained model

(i) Please see config.py file, if you want to change these parameters 

## Evaluation and testing:

cd main_code 

python3 lang_train.py --mode test --lang bengali --valRoot  create_lmdb_dataset/bengali/test_lmdb --pretrained  out/crnn_results/best_cer.pth --cuda  --out  out --adadelta

--pretrained is trained model path containing trained model

(i) Please see config.py file, if you want to change these parameters 
(ii) Path "out/test_accuracy.txt" contains  test accuracy with respect to CRR and WRR
(iii) Path "out/test_gt_and_predicted_text.txt" contains predicted output (text) of each word image. 1st column is the ground truth text and 2nd column is the predicted text
(iii) Path "out/max_prob" folder containing ".csv" file corresponding to each test word image. It provides probability values of predicted characters.
(iv) Path "out/data_prob" folder containing ".csv" file corresponding to each test word image. It provides a matrix of probability values of a test word image. Matrix dimention is (no of characters) x (length of word). If (iii) and (iv) are not required, you can skip them.    

