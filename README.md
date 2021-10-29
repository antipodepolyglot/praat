Установка Praat
===============

Praat можно бесплатно скачать и установить для разных операционных систем:

* Windows: https://www.fon.hum.uva.nl/praat/download_win.html
* Linux: https://www.fon.hum.uva.nl/praat/download_linux.html
* Mac OS: https://www.fon.hum.uva.nl/praat/download_mac.html

Установка matplotlib
====================

Для Ubuntu/Debian:

```
sudo apt-get install python3-matplotlib
```

Для Windows: установить Python 3 (https://www.python.org/downloads/), а затем:

```
pip install matplotlib
```

Анализ гласных в Praat
======================

1. Открыть аудиофайл (.mp3 или .wav) в Praat (Ctrl+O) или записать звук (Ctrl+R).

2. Добавить аннотации гласных и выделить форманты, как описано в http://www.youtube.com/watch?v=wHet9v4vMCY

3. Сохранить аннотации и форманты в текстовые файлы (Save | Save as text file...), например, `ru.Formant` и `ru.TextGrid`.

4. Запустить скрипт для рисования диаграммы.

Для средних значений формант (гласные будут отображены как точки):

```
python formant_diagram.py --formants ru.Formant --annotations ru.TextGrid --vowels_csv ru.vowels.csv --text_size 14 --average
```

Для изменения формант во времени (гласные будут отображены как ломаные линии):

```
python formant_diagram.py --formants ru.Formant --annotations ru.TextGrid --vowels_csv ru.vowels.csv --text_size 14
```

Параметры formant_diagram.py
============================

* `--formants` - файл с формантами (ooTextFile, Formant 2). Поддерживаются варианты text file и short text file.
* `--annotations` - файл с аннотациями гласных (ooTextFile, TextGrid). Поддерживаются варианты text file и short text file. Поддерживается Unicode.
* `--vowels_csv` - файл для сохранения численных значений формант. Можно не указывать.
* `--text_size` - размер шрифта. Можно не указывать - тогда используется размер по умолчанию.
* `--average` - если указан, то будут отрисованы средние значения формант для каждого гласного вместо всех значений.