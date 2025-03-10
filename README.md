# Thirdperson-info-Dataset

[日本語 README](https://github.com/IshiguroLab/Thirdperson-info-Dataset/blob/main/README_JP.md))

Thirdperson_info_Dataset is a collection of 1,399 third-person information, labeled with the level of interest and three items related to the level of interest, and displayed in Japanese.

eference:[Paper (Japanese)](https://www.anlp.jp/proceedings/annual_meeting/2025/pdf_dir/D4-3.pdf)，[Data](https://github.com/IshiguroLab/Thirdperson-info-Dataset/tree/main/data)

# Model
Four different models were created.

```
model1: Direct interest estimation model

model2: Multi-stage interest estimation model

model3: Interest estimation model for each user attribute

model4: Multi-stage interest estimation model for each user attribute
```


# Fine-tuning
Four different models were created.

Take model1 as an example.

Download `train_model1.jsonl` and `test_model1.jsonl` and execute the following code:

```
from openai import OpenAI
client = OpenAI(api_key='your_api_key')

response = client.files.create(
  file = open("train_model1.jsonl", "rb"),
  purpose = "fine-tune"
)
train_file_id = responce.id

job = client.fine_tuning.jobs.create(
  training_file = "train_file_id",
  model = "gpt-4o-2024-08-06"
)

print(job)
```

## Citation
金山凜吾, 三野星弥, 石黒浩，吉川雄一郎. 対話システムが共有する第三者情報に対するユーザの興味度推定モデルの構築. 言語処理学会第31回年次大会, 2025.
```
@InProceedings{Kanayama_nlp2025,
  author = 	"金山凜吾 and 三野星弥 and 石黒浩 and 吉川雄一郎",
  title = 	"対話システムが共有する第三者情報に対するユーザの興味度推定モデルの構築",
  booktitle = 	"言語処理学会第31回年次大会",
  year =	"2025"
}
```

## Acknowldegment
This work was supported by JSPS KAKENHI under Grant JP24H00165.

