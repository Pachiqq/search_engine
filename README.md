# search_engine
file search engine
 Поиск файлов по словам содержащимся в них.
 ## Описание
 Приложение для поиска файлов по запрашиваемым словам (requests.json) содержащимся в текстовых файлах (config.json). Результат поиска выводится в (answers.json).
## Технологии
![GitHub author](https://img.shields.io/badge/C++-14-005199?style=for-the-badge)<br>

![GitHub author](https://img.shields.io/badge/CMake-3.22-005199?style=for-the-badge)<br>
https://cmake.org/<br>

![GitHub author](https://img.shields.io/badge/JSON-3.10.5-orange?style=for-the-badge)<br>
https://github.com/nlohmann/json<br>

![GitHub author](https://img.shields.io/badge/GTest-1.11.0-green?style=for-the-badge)<br>
https://github.com/google/googletest<br>

## Building & Running
* Шаг 1: Создайте project.<br>
  * Если вы используете компилятор Visual Studio, вы можете собрать версию x64 или x32 соответственно.:<br>
    * For x64 version:<br>
`cmake -A x64 -S . -B "build64"`<br>
`cmake --build build64 --config Release`<br>
    * Для версии x32:<br>
`cmake -A Win32 -S . -B "build32"`<br>
`cmake --build build32 --config Release`<br>

  * В других случаях используйте сборку по умолчанию:<br>
`cmake -S . -B "build"`<br>
`cmake --build build --config Release`<br>

* Шаг 2: скопируйте файлы:<br>
`.requests.json`, `.config.json`, `.answers.json` и `.resources` в папку `.\bin` <br>

* Шаг 3: запустите приложение:<br>
`.Search_in_files`<br>

##  Спецификация файлов
* config.json<br>
Файл, в котором указано имя и версия приложения.<br>
Здесь вы также можете изменить максимальное количество релевантных страниц, которые будут помещены в answers.json (max_respones).<br>
Контент по умолчанию:<br>
```json
{
    "config": 
    {
        "name": "FileSearchEngine",
        "version": "0.1",
        "max_responses": 5
    },
    "files": 
    [
        "resources/file001.txt",
        "resources/file002.txt"
    ]
}
```

* requests.json<br>
Файл, в котором указаны запросы на поиск.<br>
Файл, в котором указаны запросы на поиск.<br>
Пример содержания:<br>
```json
{
    "requests":
    [
        "tiger fox",
        "wolf bird",
        "monkey"
    ]
}
```
* answers.json<br>
Файл, в который будет записан результат поиска в формате JSON.<br>
Пример содержания:<br>
```json
{
  "answers": {
    "request0": {
      "relevance": [
        {
          "docid": 1,
          "rank": 1.0
        },
        {
          "docid": 0,
          "rank": 0.6700000166893005
        }
      ],
      "result": true
    },
    "request1": {
      "relevance": [
        {
          "docid": 0,
          "rank": 1.0
        },
        {
          "docid": 1,
          "rank": 1.0
        }
      ],
      "result": true
    },
    "request2": {
      "docid": 1,
      "rank": 1.0,
      "result": true
    }
  }
}
