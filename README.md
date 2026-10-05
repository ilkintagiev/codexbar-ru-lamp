# CodexBar RU: подготовленная удалённая сборка

Пакет для разрешённого пользователем публичного репозитория `ilkintagiev/codexbar-ru-lamp` и Mac GitHub Actions сборки. Фактический запуск и результат сверяются по странице Actions.
Основа: официальный steipete/CodexBar v0.72.0, SHA cfee869f3181379dd074adb9feeb5f19a994356a, MIT, авторство upstream сохранено.

Включены только публичные исходные изменения: лампочка remaining thresholds, ранние ветви renderer для выбранного провайдера, strict Codex weekly10080 и тесты. Нет журналов, токенов, пользователей, Runtime, аккаунтов, настроек или секретов. Workflow использует обычный macos-15 GitHub-hosted runner, не larger runner. Публикация этих четырёх файлов и запуск standard Mac runner прямо разрешены пользователем.

Workflow проверяет git apply, make check, make test, package, codesign verify; создаёт ad-hoc подписанный zip и SHA256. Никакого shell-open, моделей, аккаунтов, live-Keychain тестов или публикации release. Свежий runner содержит полноценный toolchain; локальные SDK workaround не нужны.

После успешных checks и установки результата включить собственную настройку через:
`defaults write com.steipete.codexbar ruRemainingLamp -bool true`
Существующая appLanguage=ru сохраняется в пользовательских настройках. Пакет не включает локальный guarded updater: отсутствие Xcode не позволяет ему собирать будущие версии. Автоматическая доставка будущих кастомных сборок пока НЕ реализована; обычный Sparkle не должен перезаписывать кастом. Ad-hoc сборка штатно отключает Sparkle install. Официальная установленная сборка до успешной замены продолжает работать.

Непроверено: actual Actions run, сборка на runner, GUI артефакта, будущие релизы.
