# Индикаторы

___


- MACDWaveV4
  - Версия скрипта 4. (Pine script version 4)

- Шпаргалка для скриптов

  > Отрисовка идет слева направо с нуля (текущее значение `bar_index`)
     
  > Скрипт выполняется для каждого бара, поэтому текущее
    значение массива или бара начинается с текущего (`realtimebar`) и он является 0


  - Указание версии компилятору
    ```javascript
    //@version=4
    ```
  - Указание имени скрипта `study(title, shorttitle, overlay, format, precision)`
    Вызывается единожды
    - `title` - полное название скрипта 
    - `shorttitle` - сокращенное название
    - `overlay` - если `true` открывает сверху в самом графике, иначе открывается отдельным окном
    - `format` - ордината графика, возможные варианты `format.inherit, format.price, format.volume`
    - `precision` - точность и маштаб для ординаты
  - Внешняя настройка скрипта `input(title, type, defval)`
    - Возможные значения `type` 
      ``` input.bool
        input.bool
        input.color
        input.integer
        input.float
        input.string
        input.symbol
        input.resolution
        input.session
        input.source
        input.time
        ```
  - Виды серий (точек графика)
  
    `open, high, low, close, volume and time`
    
    > Работа с серией, как с массивом `[]`, позволяет откидывать
      последние значения графика `close[1] отрисует без последней(первой справа) сделки`
    
    ```text
    a = open + close // Addition of two series
    b = high / 2     // Division of a series variable by
                 // an integer literal constant
    c = close[1]     // Referring to the previous ``close`` value
    ``` 
  - Основные функции отрисовки данных
    - Простая линия `plot(series, title, color, linewidth, style, trackprice, transp, histbase, offset, join, editable, show_last, display)`
    - Отрисовка фигур `plotshape(data, style=shape.xcross)`
      - style: `flag, circle, etc...`
    - Отрисовка табличек и текста `label.new(x, y, text, xloc, yloc, color, style, textcolor, size, textalign, tooltip)`
    
  - Запрос данных, отличных от настроенный на чарте
    - Метод `security(symbol, resolution, expression, gaps, lookahead)`
    
      `symbol` -  название тикера (`текущий - syminfo.tickerid`)
      `resolution` - интервал
      `expression` - что берем (open, close, high, close)