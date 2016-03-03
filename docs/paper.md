[libjpeg](http://libjpeg.sourceforge.net), libxml, [openh264](http://www.openh264.org), [protobuf](https://developers.google.com/protocol-buffers/), [gtest](https://github.com/google/googletest), [sqlite](https://www.sqlite.org) и, конечно, [v8](https://developers.google.com/v8/), поставляются, обновляются и несложно подключаются для использования.
измемениям, какие-то меньше. Это всё же совсем не фиксированный публичный API.
Не стану останавливаться на том, как скачать код и настроить окружение, всё это подробно описано в статьях по приведенным ссылкам. Будем считать, что у нас уже есть depot_tools в нашем $PATH (нужны утилиты gn и ninja), исходный код получен и готов к сборке в директории chromium/. Сборка всего проекта Chromium нам не понадобится, по крайней мере на первом этапе.
В sample_app/src будет размещён код приложения, а все команды я буду приводить относительно текущей директории chromium/src/sample_app.
[src/sample_app.cc](https://github.com/dreamer-dead/chromium-sample-app/blob/470736619faaba62561d552b16665fdb69a0fe5a/src/sample_app.cc)
```c++
int main() {
  return 0;
}
```
[src/BUILD.gn](https://github.com/dreamer-dead/chromium-sample-app/blob/8248c8550ea99887b555776c1c4a4e1da91259bd/src/BUILD.gn)
```c++
# SampleApp

executable("sample_app") {
  output_name = "sample_app"
  sources = [
    "sample_app.cc",
  ]
}
описывающих этапы сборки проекта. GN — это следующий этап развития генератора 
ninja-файлов, он гораздо быстрее GYP, написан на С++ вместо Python, и его синтаксис
В своем билд-конфиге sample_app/src/BUILD.gn задаём имя таргета, итоговое имя исполняемого файла и 
перечисляем файлы с исходным кодом.
[src/root_BUILD_gn.patch](https://github.com/dreamer-dead/chromium-sample-app/blob/d346775d3392a9082c53b45547f53903e69dd5bd/src/root_BUILD_gn.patch)