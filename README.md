The code is the implementation of NeuralCDM model, and the data set is based on student responses from four classes over a semester in a course called "**Modern Educational Technology and Applications**".

## Process:

- The crawler was used to obtain the answer data of four classes in a semester in **Modern Educational Technology and Applications**
- By consulting relevant experts, mark the **Q matrix** according to the answer data
- According to the Q matrix, the answer data is encoded into "0-1" JSON format
- The annotated data is partitioned by divide_data.py in NeuralCD
- Run the partitioned data in NeuralCD

## Dependencies:

- python 3.6
- pytorch >= 1.0 (pytorch 0.4 might be OK but pytorch<0.4 is not applicable)
- numpy
- json
- sklearn

## Usage

Run divide_data.py to divide the original data set data/log_data.json into train set, validation set and test set. The data/ folder has already contained divided data so this step can be skipped.

```
python divide_data.py
```

Train the model:

```
python train.py {device} {epoch}
```

For example:

```
python train.py cuda:0 5` or `python train.py cpu 5
```

Test the trained the model on the test set:

```
python predict.py {epoch}
```

# Data Set

The data/log_data.json is based on student responses from four classes over a semester in a course called "**Modern Educational Technology and Applications**".When a user answers a problem for multiple times, only the first time is kept. The logs are organized in the structure:

- log_data.json = [user1, user2, ...]
- user = {"user_id": user_id, "log_num": log_num, "logs": [log1, log2, ...]]}
- log = {"exer_id": exer_id, "score": score, "knowledge_code": [knowledge_code1, knowledge_code1, ...]}

The ids/codes are recoded starting from 1.

## Details

```xml
# Number of Students, Number of Exercises, Number of Knowledge Concepts
176,79,5
```

- Students with less than 15 logs would be deleted in divide_data.py.
- The model parameters are initialized with Xavier initialization.
- The model uses Adam Optimizer, and the learning rate is set to 0.002.