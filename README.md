## Training, Finetuning and Evaluation:


## Dataset preparation:
- Create LMDB files for train, validation and test dataset splits.
Please follow README under "create_lmdb_dataset" folder

## Pretrained Models:
- You can find the pretrained models for V4 printed for 13 languages under the Assets.

## Evaluation and testing:

```bash
cd main_code 

python3 lang_train.py --mode test --lang bengali --valRoot  create_lmdb_dataset/bengali/test_lmdb --pretrained  out/crnn_results/best_cer.pth --cuda  --out  out --adadelta
```
`--pretrained` is trained model path containing trained model

- Please see config.py file, if you want to change these parameters 
- Path "out/test_accuracy.txt" contains  test accuracy with respect to CRR and WRR
- Path "out/test_gt_and_predicted_text.txt" contains predicted output (text) of each word image. 1st column is the ground truth text and 2nd column is the predicted text
- Path "out/max_prob" folder containing ".csv" file corresponding to each test word image. It provides probability values of predicted characters.
- Path "out/data_prob" folder containing ".csv" file corresponding to each test word image. It provides a matrix of probability values of a test word image. Matrix dimention is (no of characters) x (length of word). If (iii) and (iv) are not required, you can skip them.    

## Contact

You can contact **[Ajoy Mondal](mailto:ajoy.mondal@iiit.ac.in)** at for any issues or feedbacks.
