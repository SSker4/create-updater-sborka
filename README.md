<div align="center">
  <img src="src/main/resources/assets/modpackupdater/textures/gui/update_icon.png" width="72" height="72" alt="Modpack Updater icon" />
  <h1>Modpack Updater</h1>
  <p><b>Приватный апдейтер сборки Minecraft для закрытого сервера.</b></p>
  <p>
    <img alt="Minecraft" src="https://img.shields.io/badge/Minecraft-1.21.1-44cc11?style=for-the-badge" />
    <img alt="NeoForge" src="https://img.shields.io/badge/NeoForge-21.1.235-ff7f2a?style=for-the-badge" />
    <img alt="Platform" src="https://img.shields.io/badge/Windows-only-1f6feb?style=for-the-badge" />
    <img alt="Private" src="https://img.shields.io/badge/Private-server-red?style=for-the-badge" />
  </p>
</div>

---

<div align="center">
  <h2>Важное предупреждение</h2>
  <p>
    <b>Этот проект сделан для приватного Minecraft-сервера и конкретной сборки.</b><br />
    Если вы не участник сервера, не знаете автора сборки или не понимаете, что именно скачиваете, не устанавливайте этот мод и не запускайте обновление.
  </p>
</div>

---

<div align="center">
  <table>
    <tr>
      <td><b>Назначение</b></td>
      <td>Обновление файлов модпака через GitHub Releases</td>
    </tr>
    <tr>
      <td><b>Сервер</b></td>
      <td>Приватный, доступ только для своих игроков</td>
    </tr>
    <tr>
      <td><b>GitHub repo</b></td>
      <td><a href="https://github.com/SSker4/create-updater-sborka">SSker4/create-updater-sborka</a></td>
    </tr>
    <tr>
      <td><b>API</b></td>
      <td><code>https://api.github.com/repos/SSker4/create-updater-sborka/releases/latest</code></td>
    </tr>
    <tr>
      <td><b>Файл обновления</b></td>
      <td>первый asset релиза: <code>latest.zip</code></td>
    </tr>
    <tr>
      <td><b>Локальная версия</b></td>
      <td><code>config/modpackupdater-version.json</code></td>
    </tr>
  </table>
</div>

## Что Это

`Modpack Updater` добавляет маленькую кнопку обновления в главное меню Minecraft. Кнопка появляется только на Windows и открывает отдельный экран проверки версии сборки.

Мод не обновляет сам себя. Он обновляет именно файлы сборки: моды, которые лежат в архиве `latest.zip` последнего GitHub Release.

## Для Кого

Этот мод предназначен для игроков приватного сервера, которые получили сборку от администрации сервера.

Если вы нашли этот репозиторий случайно:

- не качайте файлы без понимания, откуда они и зачем нужны;
- не ставьте `latest.zip` в свою сборку;
- не используйте мод вне приватного сервера;
- не ждите совместимости с другими модпаками.

## Как Работает

<div align="center">
  <table>
    <tr>
      <td align="center"><b>1</b></td>
      <td>Игрок запускает Minecraft на Windows</td>
    </tr>
    <tr>
      <td align="center"><b>2</b></td>
      <td>В главном меню появляется маленькая кнопка обновления</td>
    </tr>
    <tr>
      <td align="center"><b>3</b></td>
      <td>Мод проверяет последний релиз GitHub</td>
    </tr>
    <tr>
      <td align="center"><b>4</b></td>
      <td>Сравнивает локальную версию с тегом релиза</td>
    </tr>
    <tr>
      <td align="center"><b>5</b></td>
      <td>Если версии разные, скачивает <code>latest.zip</code></td>
    </tr>
    <tr>
      <td align="center"><b>6</b></td>
      <td>Распаковывает файлы в папку <code>mods</code></td>
    </tr>
  </table>
</div>

## Правила Обновления

- Все файлы из `latest.zip` копируются в папку `mods`.
- Если файл с таким же именем уже есть, он заменяется новым.
- Файлы в `mods`, которых нет в архиве, не удаляются.
- После успешной установки обновляется локальная версия.
- После обновления игрок должен перезапустить игру.

## Что Заливать В GitHub Release

В релиз нужно заливать один главный asset:

```text
latest.zip
```

Внутри архива должны лежать файлы модов сборки:

```text
latest.zip
├── create-xxxxx.jar
├── jei-xxxxx.jar
├── architectury-xxxxx.jar
├── sodium-xxxxx.jar
└── другие-моды-сборки.jar
```

Не кладите в `latest.zip` сам updater-мод:

```text
modpackupdater-1.0.0.jar
```

## Формат Релиза

Пример релиза:

```text
Tag: v1.0.1
Title: Сборка 1.0.1
Asset #1: latest.zip
```

Можно использовать тег без буквы `v`:

```text
Tag: 1.0.1
```

Мод сам убирает ведущую `v` перед сравнением версий.

## Локальная Версия Игрока

Файл:

```text
config/modpackupdater-version.json
```

Формат:

```json
{
  "version": "1.0.0"
}
```

Если файла нет, версия считается `0.0.0`.

## Что Класть В Сборку Игроку

Минимально:

```text
mods/modpackupdater-1.0.0.jar
config/modpackupdater-version.json
```

Остальные моды сборки кладутся как обычно.

## Интерфейс

<div align="center">
  <table>
    <tr>
      <td align="center"><b>Главное меню</b></td>
      <td align="center"><b>Экран обновления</b></td>
    </tr>
    <tr>
      <td>Маленькая кнопка рядом с настройками, в стиле ванильного GUI.</td>
      <td>Тёмный экран, градиентный заголовок, текущая версия, последняя версия, статус обновления.</td>
    </tr>
  </table>
</div>

## Сборка Мода

```powershell
.\gradlew.bat build --no-daemon --stacktrace
```

Готовый файл:

```text
build/libs/modpackupdater-1.0.0.jar
```

## Технические Детали

- Minecraft: `1.21.1`
- Loader: `NeoForge 21.1.235`
- Java: `21`
- HTTP: `java.net.http.HttpClient`
- JSON: `Gson`
- GitHub source: `SSker4/create-updater-sborka`
- Работает только на Windows
- На macOS и Linux кнопка не регистрируется

---

<div align="center">
  <p><b>Проект для своего сервера. Не ставьте его в чужие сборки без понимания, что именно обновляется.</b></p>
</div>
