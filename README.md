# building_exe_kivy
Нужные модули:

setuptools

wheel

kivy

pyinstaller

pycrypto
# Изменения некоторых файлов в site_packages
Перейдите по пути C:\Users\имя_компьютера\AppData\Local\Programs\Python\Python39\Lib\site-packages\kivy\deps

Откройте файл __unit__.py редактором и добавте следующие строки:

import sdl2
import glew

После установите модуль tinyaes

pip install tinyaes
## Важно, для установки модулей нужен Windows 10 SDK build tools

# Компиляция
В папке с проектом создайте папку src и перенесите все файлы проекта в неё.
Дальше вам нужно скачать spec файл: https://drive.google.com/file/d/15yt15IZPLcq5A61meWWFVkkX1mMAIwzP/view?usp=sharing

Как это будет выглядеть:

![image](https://user-images.githubusercontent.com/63918733/132127147-18f262f0-bce3-4865-a8c2-c2c708037b93.png)


В самом spec файлы нужно изменить следующие строки:

Названия приложения

app_name = 'rbplay'

Все дополнительные файлы, которые должны быть включены в exe

added_files = [
         ( 'src\\devices_list.json', '.'),
         ( 'src\\settings\\devices_list.json', '.'),
         ( 'src\\settings\\states.json', '.'),
         ( 'src\\lock_screen\\states.json', '.'),
         ] 
         
Путь к папке с проектом

pathex=['C:\\Users\\имя_компьютера\\Desktop\\rbplay-master']

Важно, указывать путь нужно не к src папке, а к начальной, где находится сама папка src

После открываем консоль и в ней переходим в нашу папку с spec файлом

Пример:

cd C:\\Users\\имя_компьютера\\Desktop\\rbplay-master

Вводим команду

python -m PyInstaller single.spec

После ждем компиляции всего проекта, exe появится в папке dist

Готово)
# Некоторые дополнительные моменты
Если у вас заданы пути к вашим json файлам в коде, то задайте переменную, в ней будет хранится путь к временным файлам.

TEMP_FOLDER = str(sys._MEIPASS).replace('\\', '/') + '/'

И добавте её ко всем путям, пример:

with open(TEMP_FOLDER + 'settings/states.json', 'w', encoding='utf16') as write_data_file:

До этого импортируйте модуль sys

import sys

Скорее всего ваш редактор кода будет ругаться, что в модули sys нет _MEIPASS, но дело в том, что его добавляет сам pyinstaller и он может существовать только уже готовом исходнике.
