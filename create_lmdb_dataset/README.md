## Training, Finetuning and Evaluation:


## Dataset preparation:
- Create LMDB files for train, validation and test dataset splits.
Please follow README under "create_lmdb_dataset" folder 

(i) please create "bengali/train_images.txt" file containing path of training word images. Each row of the file contains path of each word image in training set

(ii) please create "bengali/train_labels.txt" file containing ground truth trascription of training word images. Each row of the file contains transcription of each word image in training set

(iii) please create "bengali/val_images.txt" file containing path of validation word images. Each row of the file contains path of each word image in validation set

(iv) please create "bengali/val_labels.txt" file containing ground truth trascription of validation word images. Each row of the file contains transcription of each word image in validation set

(v) please create "bengali/test_images.txt" file containing path of test word images. Each row of the file contains path of each word image in test set

(vi) please create "bengali/test_labels.txt" file containing ground truth trascription of test word images. Each row of the file contains transcription of each word image in test set

#####Create LMDB Training, Validation and Test files 

cd create_lmdb_dataset

#To create train_lmdb 

python3  create_lmdb_dataset  --type train

(i) It creates "train_lmdb" file under "bengali" folder 

#To create val_lmdb 

python3  create_lmdb_dataset  --type val

(i) It creates "val_lmdb" file under "bengali" folder 


#To create test_lmdb 

python3  create_lmdb_dataset  --type test

(i) It creates "test_lmdb" file under "bengali" folder 
