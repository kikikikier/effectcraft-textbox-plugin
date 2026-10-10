# TextBox Plugin for EffectCraft

Плашка под текст с независимым Matte.

TextBox 1.1 встроен в реестр эффектов. Отрицательные отступы позволяют сделать плашку меньше текста. Геометрический Matte учитывает скругления и смещение, но не зависит от прозрачности заливки. Параметры поддерживают ключевые кадры и выражения.

TextBox plugin for EffectCraft with signed padding and a geometric matte independent of fill opacity.

## Применение

Патч рассчитан на [EffectCraft](https://github.com/storytold/effectcraft) commit `608d1b077b65bb7591f26be587a2a5a47f4278bc`.
Он применяется отдельно от двух других функциональных патчей. Готовые исходники со всеми
изменениями и Windows-сборка: [effectcraft-custom](https://github.com/kikikikier/effectcraft-custom).

```powershell
git clone https://github.com/kikikikier/effectcraft-textbox-plugin.git
git clone https://github.com/storytold/effectcraft.git
Set-Location effectcraft
git checkout 608d1b077b65bb7591f26be587a2a5a47f4278bc
git apply --check ../effectcraft-textbox-plugin/effectcraft-textbox-plugin.patch
git apply ../effectcraft-textbox-plugin/effectcraft-textbox-plugin.patch
# Общая правка оформления применяется один раз, даже если установлены несколько патчей.
git apply ../effectcraft-textbox-plugin/custom-build-branding.patch
cargo +1.95.0 build --locked --release -p effectcraft
```

Патчи не предназначены для произвольной новой версии upstream без проверки совместимости.
Если распространяете свою изменённую сборку, удалите также файлы фирменных знаков из
`docs/brand/` и их изображения в документации согласно условиям upstream.

## Проверка

```powershell
cargo +1.95.0 test --release -p effectcraft-text-box --lib -p effectcraft-host --test text_box --test plugins
```

Проверена применимость каждого патча к чистому базовому commit и совместимость всех трёх
патчей во всех шести порядках применения. Подробности проверки общей сборки — в
[отчёте](https://github.com/kikikikier/effectcraft-custom/blob/main/CUSTOM-BUILD.md).

## Связанные репозитории

- [effectcraft-infinite-drag](https://github.com/kikikikier/effectcraft-infinite-drag)
- [effectcraft-type-in-font-search](https://github.com/kikikikier/effectcraft-type-in-font-search)
- [Все изменения вместе](https://github.com/kikikikier/effectcraft-custom)

## Происхождение и лицензия

Основано на EffectCraft команды ArtCraft и участников проекта. Это независимые изменения,
а не официальный релиз upstream. Лицензия кода: **MIT OR Apache-2.0**; уведомления об авторстве
сохранены в [NOTICE](NOTICE), [LICENSE-MIT](LICENSE-MIT) и [LICENSE-APACHE](LICENSE-APACHE).
