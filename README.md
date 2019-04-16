# speech_recognition

Для обучения акустической модели использовалась имплементация DeepSpeech2 на PyTorch из репозитория https://github.com/SeanNaren/deepspeech.pytorch

В качестве обучающего датасета использовался VoxForge. Датасет был разделен на обучающую и тестовую части.

>параметры при обучении модели:
>hidden-layers=5
>epochs=20
>batch-size=20
>Обученная модель доступна по ссылке https://yadi.sk/d/I5lCZ9mvN7DF8g

для оценки точности модели: 
python test.py --model-path models/deepspeech_final.pth --test-manifest data/voxforge_validation_manifest.csv --cuda --verbose

В качестве лингвистической модели был использовал KenLm https://github.com/kpu/kenlm
Модель строилась по датасету http://mattmahoney.net/dc/text8.zip
Итоговая модель в формате ARPA https://yadi.sk/d/yqHccjREzlkSWw
бинарный файл модели https://yadi.sk/d/Jvr4dFkxe5PWxA

для использования лингвистической модели в DeepSpeech2:
python test.py --model-path models/deepspeech_final.pth --test-manifest data/voxforge_validation_manifest.csv --cuda --verbose --lm-path ../kenlm/build/text_5gram.binary  --decoder beam



