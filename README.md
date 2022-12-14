# Nginxの手動インストールについて

## Nginxのインストール
-yはインストールに自動的にyesを選択する  
--no-install-recommendsは必須でないパッケージのインストールを拒否する
```bash
apt install -y --no-install-recommends ufw

apt install -y --no-install-recommends nginx

//途中にタイムゾーンを選択する必要がある
Please select the geographic area in which you live. Subsequent configuration questions will narrow this down by presenting a list of cities, representing the time zones in which they
are located.

  1. Africa  2. America  3. Antarctica  4. Australia  5. Arctic  6. Asia  7. Atlantic  8. Europe  9. Indian  10. Pacific  11. SystemV  12. US  13. Etc
Geographic area: 6

Please select the city or region corresponding to your time zone.

  1. Aden      10. Bahrain     19. Chongqing  28. Harbin       37. Jerusalem    46. Kuala_Lumpur  55. Novokuznetsk  64. Qyzylorda      73. Taipei         82. Ulaanbaatar
  2. Almaty    11. Baku        20. Colombo    29. Hebron       38. Kabul        47. Kuching       56. Novosibirsk   65. Rangoon        74. Tashkent       83. Urumqi
  3. Amman     12. Bangkok     21. Damascus   30. Ho_Chi_Minh  39. Kamchatka    48. Kuwait        57. Omsk          66. Riyadh         75. Tbilisi        84. Ust-Nera
  4. Anadyr    13. Barnaul     22. Dhaka      31. Hong_Kong    40. Karachi      49. Macau         58. Oral          67. Sakhalin       76. Tehran         85. Vientiane
  5. Aqtau     14. Beirut      23. Dili       32. Hovd         41. Kashgar      50. Magadan       59. Phnom_Penh    68. Samarkand      77. Tel_Aviv       86. Vladivostok
  6. Aqtobe    15. Bishkek     24. Dubai      33. Irkutsk      42. Kathmandu    51. Makassar      60. Pontianak     69. Seoul          78. Thimphu        87. Yakutsk
  7. Ashgabat  16. Brunei      25. Dushanbe   34. Istanbul     43. Khandyga     52. Manila        61. Pyongyang     70. Shanghai       79. Tokyo          88. Yangon
  8. Atyrau    17. Chita       26. Famagusta  35. Jakarta      44. Kolkata      53. Muscat        62. Qatar         71. Singapore      80. Tomsk          89. Yekaterinburg
  9. Baghdad   18. Choibalsan  27. Gaza       36. Jayapura     45. Krasnoyarsk  54. Nicosia       63. Qostanay      72. Srednekolymsk  81. Ujung_Pandang  90. Yerevan
Time zone: 79
```

## ファイアウォールの調整
```bash
ufw app list

Available applications:
  Nginx Full
  Nginx HTTP
  Nginx HTTPS
```
- Nginx Full:このプロファイルは、port80とport443の両方を開く
- Nginx HTTP：このプロファイルは、port80のみ開く
- Nginx HTTPS：このプロファイルは、port443のみ開く

```bash
ufw allow 'Nginx HTTP'
ufw status
```

## ページが表示されるか確認する
```bash
curl localhost

<!DOCTYPE html>
<html>
<head>
<title>Welcome to nginx!</title>
<style>
    body {
        width: 35em;
        margin: 0 auto;
        font-family: Tahoma, Verdana, Arial, sans-serif;
    }
</style>
</head>
<body>
<h1>Welcome to nginx!</h1>
<p>If you see this page, the nginx web server is successfully installed and
working. Further configuration is required.</p>

<p>For online documentation and support please refer to
<a href="http://nginx.org/">nginx.org</a>.<br/>
Commercial support is available at
<a href="http://nginx.com/">nginx.com</a>.</p>

<p><em>Thank you for using nginx.</em></p>
</body>
</html>
```