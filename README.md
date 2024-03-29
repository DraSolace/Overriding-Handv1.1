# Overriding-Handv1.1
###### (на самом деле v1.1.3.9)
*Overriding hand - моя маленькая мечта. Я долго засматривался на [AHK](https://www.autohotkey.com), но мне совсем не нравилось "вручную" создавать\хранить\запускать\изменять\удалять скрипты. А жухлая и зажеванная документация делу точно не помогала.*

К тому же, я использовал AHK для совсем базовых вещей. ~~Обычно для игр~~. Мне нужен был легкий в использовании, примитивный инструмент.

**_Ну вот я про себя и подумал:_**
> "Да наверняка создать собственный язык дело плевое"


## И что же это за чудо?
Клиент-макросник c ***неплохим*** GUI на чистом питоне, который умеет:

* *Создавать* \ *изменять* \ *удалять* макросы из интерфейса
* *Запускать* и *отслеживать* запущенные макросы из интерфейса
* Сверху это всё дело приправлено **DMS** и **Panic Button** для полного контроля происходящего

Эти макросы создаются на собственном "языке программирования" - **Overscript**. Подробная документация с кучей примеров и разбором разных ситуаций встроена прямо в приложение!

![](https://media.giphy.com/media/IoAFDKJR8XbtO8LhtA/giphy.gif)

Функционально макросы способы на довольно гибкую эмуляцию любых нажатий клавы\мыши\колесика\комбинаций всего перечисленного + движений курсора. Ничего навороченного вроде функций, циклов или переменных нет. Гибкость заключается в разных режимах работы и директивах.

**Overscript** был умышленно сделан примитивным, но высокоуровневым. Любой пользователь может не напрягаясь накидать пару команд и получить нужный результат. А если что - местный "компилятор" выдаст тебе наводящую ошибку.
Создать прямо таки IDE с хайлайтами и контекстуальными подсказками мне не под силу, масенький я ещё. Но этого ***минимума*** должно хватить. А даже если имея ошибку компилятора на руках вы не понимаете в чем проблема - ничего не помешает свериться с документацией и продолжить написание своего макроса :)

![](https://media.giphy.com/media/wRe839uv0144kyyxaA/giphy.gif)

Есть в Overriding hand ещё много разных маленьких приспособ для пущего удобства, но лучше откройте их для себя сами :)



## База данных! 
Посколько это будет моей дипломной работой (в требования которой называли наличие базы данных), *ТУТ ЕСТЬ БД*!

Помимо бесполезной информации о пользователях и их действиях, туда записываются  ***АБСОЛЮТНО ВСЕ***  итерации макросов, и остаются там даже если макрос уже удален.
Разрастись ей хотя бы до 5Мб будет сложно, за это не беспокойся. Она будет создана при запуске в папке bin. 
На выходе база sqlite'овская.

## Много требует? Безопасен? 
Тут тоже все крутяк, этот бедолага ест не больше 70Мб, а ЦП его вообще не замечает. А как только вызывается closeEvent, его (и всего что с ним связано) след простынет, абсолютно всё высвобождается; и я позаботился о том, что бы closeEvent всегда был замечен.

Но даже если каким-то чудом возникнет ЧП - в программе существует DMS.
И автор совсем не злился в процессе его тестирования :)

<img src="https://media.giphy.com/media/wDJ03HfEWDf3WIYYqe/giphy.gif" width="400" height="250" />

Одна дилемма - некоторые шибко чувствительные антивирусы (например оранжевый) могут озвереть. Дай им просканировать директорию, и они скажут что всё окей.

## Зависимости
1. [keyboard](https://github.com/boppreh/keyboard) + [mouse](https://github.com/boppreh/mouse)
2. [PyQt5](https://www.riverbankcomputing.com/software/pyqt/)
   + или забить, если есть [PySide2](https://github.com/raccoonmonk/pyside2). Использовал я обе (по-чёрному оверрайдил, делал перегрузки и нарушал все принципы ООП).

## Собранный билд
Если ты гигачад, что плюётся желчью от одного лишь упоминания питона(как же я тебя понимаю, братан), или у тебя просто нет питона\не хочется с этим ковырятся - у этого репозитория есть [бранч "Built"](https://github.com/DraSolace/Overriding-Handv1.1/tree/Built). Там ***уже собранный*** в exe файл билд. Можно просто скачать и запускать.
