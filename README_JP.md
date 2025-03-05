# 第三者情報データセット

Thirdperson_info_Datasetは、1,399件の第三者情報を集めたもので、興味度と、興味度に関連する3つの項目がラベル付けされ、日本語で表示されている。

参考：[論文](https://www.anlp.jp/proceedings/annual_meeting/2025/pdf_dir/D4-3.pdf)，[データ](https://github.com/IshiguroLab/Thirdperson-info-Dataset/tree/main/data)

# モデル
4種類のモデルを作成した。

```
model1： 直接興味度推定モデル

model2： 多段階興味度推定モデル

model3： ユーザ属性ごとの興味度推定モデル

model4: ユーザ属性ごとの多段階興味度推定モデル
```

# Fine-tuning
4種類のモデルを作成した。

model1を例に説明する。

`train_model1.jsonl`と`test_model1.jsonl`をダウンロードし、以下のコードを実行する：

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

# Citation
金山凜吾, 三野星弥, 石黒浩，吉川雄一郎. 対話システムが共有する第三者情報に対するユーザの興味度推定モデルの構築. 言語処理学会第31回年次大会, 2025.
```
@InProceedings{Kanayama_nlp2025,
  author = 	"金山凜吾 and 三野星弥 and 石黒浩 and 吉川雄一郎",
  title = 	"対話システムが共有する第三者情報に対するユーザの興味度推定モデルの構築",
  booktitle = 	"言語処理学会第31回年次大会",
  year =	"2025"
}
```

# 謝辞
本研究は、日本学術振興会科研費（JP24H00165）の助成を受けた。

