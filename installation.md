Upload the one in the pterodactyl folder in the /var/www/pterodactyl folder of your vps

Open /var/www/pterodactyl/resources/views/templates/wrapper.blade.php

Search 
        <link rel="apple-touch-icon" sizes="180x180" href="/favicons/apple-touch-icon.png">
        <link rel="icon" type="image/png" href="/favicons/favicon-32x32.png" sizes="32x32">
        <link rel="icon" type="image/png" href="/favicons/favicon-16x16.png" sizes="16x16">
        <link rel="manifest" href="/favicons/manifest.json">
        <link rel="mask-icon" href="/favicons/safari-pinned-tab.svg" color="#bc6e3c">
        <link rel="shortcut icon" href="/favicons/favicon.ico">

Replace it with 
        <link rel="manifest" href="/favicons/manifest.json">
        <link rel="icon" type="image/png" id="esmileimage" href="#">
        <link rel="mask-icon" href="/favicons/safari-pinned-tab.svg" color="#bc6e3c">

Search
    </head>

Put down
<script type="text/javascript">
        fetch('/esmile/icon.json')
        .then(response => response.json())
        .then(data => {
                document.getElementById('esmileimage').href=data.icon;
        });
    </script>

Save and close the file

Open /var/www/pterodactyl/resources/views/layouts/admin.blade.php

Search
        <link rel="apple-touch-icon" sizes="180x180" href="/favicons/apple-touch-icon.png">
        <link rel="icon" type="image/png" href="/favicons/favicon-32x32.png" sizes="32x32">
        <link rel="icon" type="image/png" href="/favicons/favicon-16x16.png" sizes="16x16">
        <link rel="manifest" href="/favicons/manifest.json">
        <link rel="mask-icon" href="/favicons/safari-pinned-tab.svg" color="#bc6e3c">
        <link rel="shortcut icon" href="/favicons/favicon.ico">

Replace it with
        <link rel="manifest" href="/favicons/manifest.json">
        <link rel="mask-icon" href="/favicons/safari-pinned-tab.svg" color="#bc6e3c">
        <link rel="icon" type="image/png" id="esmileimage" href="#">

Search
    </head>

Put down
<script type="text/javascript">
        fetch('/esmile/icon.json')
        .then(response => response.json())
        .then(data => {
                document.getElementById('esmileimage').href=data.icon;
        });
    </script>

Save and close the file


How to put the custom icon

Open /var/www/pterodactyl/public/esmile/icon.json

Search
"icon": "https://cdn.discordapp.com/attachments/851919671878746112/955534101627162624/pterodactylicon.png"

Replace the link with the image you like as the panel icon

https://cdn.discordapp.com/attachments/851919671878746112/955534101627162624/pterodactylicon.png

Save and close the file

Terminal command:

cd /var/www/pterodactyl
php artisan down
php artisan migrate --seed --force
yarn install
yarn build:production
php artisan config:cache
php artisan view:cache
php artisan queue:restart
php artisan up


Once set, if it does not load, use control + f5 3 or 4 times to reload the page cache and load correctly.