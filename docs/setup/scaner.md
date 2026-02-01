# Настройка параметров работы сканера

Чтобы при выполнении процесса сканирования в автоматическом режиме оно осуществлялось с корректными настройками сканера (разрешение, цветность и т.п.), можно предварительно прописать необходимые значения параметров в файле настройки сканера *PassportReader.scanner.config*, входящего в состав утилиты.

Пример содержимого файла настроек *PassportReader.scanner.config*:

```<?xml version="1.0" encoding="utf-8" ?>
<scan-settings 
interface-type="None" 
brightness-control="Manual"
brightness="5"
compression="NoCompression"
orientation="Portrait"
paper-size="None"
paper-top="0" 
paper-left="0" 
paper-bottom="14000" 
paper-right="9000" 
picture-mode="GrayScale"
resolution="300"
rotation-angle="Rotation90"
softrotation-angle="Rotation0"
source="0"
template-name="Passport_RU"
/>```

Назначение параметров, задаваемых в файле настройки, следующее:

* **interface-type** – тип диалога сканирования, допустимые значения: None – без диалога, только указанные настройки, Twain – стандартный диалог сканера (все прочие настройки игнорируются).
* **brightness-control** – режим яркости изображения, допустимые значения: Fine – регулируется автоматически утилитой, Scanner – регулируется автоматически сканером, Manual – настраивается вручную через значение параметра brightness.
* **compression** – определяет, использовать ли аппаратное сжатие изображения при сканировании, допустимые значения: CcittGroup3, CcittGroup4, JpegJfif, NoCompression. Необходимо иметь ввиду, что данный параметр поддерживается не всеми сканерами.
* **orientation** – ориентация изображения, допустимые значения: Landscape, Portrait.
* **paper-size** – размер бумаги. Устанавливает одно из значений размера бумаги. Используются международные названия, приведённые ниже, либо Custom – для ручного задания размера через параметры paper-top, paper-left, paper-right, paper-bottom. Допустимые значения: A0, A1, A2, A3, A4, A5, B1_ISO, B2_ISO, B3_ISO, B4_ISO, B4_JIS, B5_ISO, B5_JIS, B6_ISO, B6_JIS, C3, C4, C5, C6, Custom, DL, Envelope10, Envelope11, Envelope12, Envelope14, Envelope9, EnvelopeCheck, EnvelopeMonarch, Executive, Fanfold, Folio, GermanFanfold, GermanLegalFanfold, Legal, Letter, None, QUARTO, RA2, RA3, RA4, Slide, Statement, Tabloid.
* **picture-mode** – цветность сканируемого изображения, допустимые значения: BlackAndWhite – черно-белое изображение, Grayscale – оттенки серого, Color – цветное изображение.
* **resolution** – разрешение сканирования, задается  в количестве точек на дюйм. Строго рекомендуется использовать только разрешение в 300dpi, при установке иного разрешения, распознавание не гарантируется. Допустимые значения (все кроме 300 – будет сканировать, но могут быть проблемы с распознаванием): 200, 300, 400, 500, 600.
* **rotation-angle** – аппаратный поворот отсканированного изображения, допустимые значения: Rotation0 – не поворачивать, Rotation90 – повернуть на 90 градусов, Rotation180 – повернуть на 180 градусов, Rotation270 – повернуть на 270 градусов. Необходимо иметь ввиду, что данный параметр поддерживается не всеми сканерами.
* **softrotation-angle-comment** – программный поворот отсканированного изображения,  допустимые значения: Rotation0 – не поворачивать, Rotation90 – повернуть на 90 градусов, Rotation180 – повернуть на 180 градусов, Rotation270 – повернуть на 270 градусов.
* **source-comment** – Id выбранного сканера, допустимые значения: 0, 1, 2...
* **template-name-comment** – название шаблона распознавания, допустимые значения: Passport_RU.

Для удобства настройки непосредственно в файле *PassportReaderService.scanner.config* по каждому параметру есть подробный комментарий с возможными вариантами значений параметра, например: 

```...
picture-mode-comment="Цветность сканируемого изображения". BlackAndWhite – черно-белое изображение, Grayscale – оттенки серого, Color – цветное изображение."
picture-mode="GrayScale"
...```
