Виртуальный тур «Транснефть — Тюмень»

Состав
  index.html  — страница тура
  app.js      — код и все библиотеки (three.js и др.), интернет посетителю не нужен
  tour.glb    — модель зала (15 МБ)

Как выложить
  1. Скопировать все три файла в одну папку на сервере (например, /var/www/tour/).
  2. Открыть https://ваш-сервер/tour/ — откроется index.html.
  Работает на любом статическом сервере (nginx, Apache, IIS, хостинг).
  С диска двойным кликом не откроется: браузер не загружает модель по file://.

Желательно (ускоряет загрузку модели: 15 МБ -> ~10 МБ по сети)
  nginx, в блок server или location:
      gzip on;
      gzip_types application/javascript model/gltf-binary application/octet-stream;
      types { model/gltf-binary glb; }

  Apache (.htaccess):
      AddType model/gltf-binary .glb
      AddOutputFilterByType DEFLATE application/javascript model/gltf-binary

Если тур вставляется в другую страницу через iframe, добавьте атрибуты:
  <iframe src="/tour/" allow="fullscreen" allowfullscreen style="width:100%;height:600px;border:0"></iframe>
