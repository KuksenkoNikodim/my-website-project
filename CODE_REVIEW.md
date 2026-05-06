# my-website-project
# Ветеринарная больница — страница приветствия

**Учебный проект**  
Автор: KuksenkoNikodim  
Дата: 05.05.2026
## День 7: Работа над проектом
---
# CODE_REVIEW — Проверка кода functions.php

## Дата проверки
06.05.2026

![Скриншот дня 7](./День%207.png)

### Что сделано:
- Обновлена структура проекта
- Добавлены новые файлы
- Настроены Packages

## Что проверили
- [x] Наличие PHPDoc-комментариев перед каждой функцией
- [x] Наличие строчных комментариев (//) внутри функций
- [x] Все строки заканчиваются точкой с запятой ;
- [x] Отсутствие лишних пробелов и пустых строк
- [x] Шорткод [приветствие] работает корректно

## Результаты проверки

### Найденные замечания:
*Замечаний нет* — всё соответствует стандартам PHP и WordPress Coding Standards.

### Что исправили:
Ничего не потребовалось исправлять.

## Проверенная функция

/**
 <?php
// ===== ШОРТКОДЫ ДЛЯ УЧЕБНОЙ ПРАКТИКИ (День 7) =====

// Шорткод [moi_stati] - список последних 5 статей
function pokazat_stati() {
    $stati = get_posts( array('numberposts' => 5) );
    if ( empty($stati) ) {
        return '<p>📭 Пока нет статей. Добавьте первую запись!</p>';
    }
    $rezultat = '<ul style="list-style: disc; padding-left: 20px;">';
    foreach ( $stati as $stat ) {
        $rezultat .= '<li><a href="' . get_permalink($stat) . '">' . $stat->post_title . '</a></li>';
    }
    $rezultat .= '</ul>';
    return $rezultat;
}
add_shortcode('moi_stati', 'pokazat_stati');

// Шорткод [statistika] - статистика сайта
function statistika_sayta() {
    $kol_state = wp_count_posts()->publish;
    $kol_stranits = wp_count_posts('page')->publish;
    return '<div style="background: #f0f0f0; padding: 15px; border-radius: 8px; border-left: 4px solid #4CAF50;">
        <p>📄 <strong>Статей на сайте:</strong> ' . $kol_state . '</p>
        <p>📑 <strong>Страниц на сайте:</strong> ' . $kol_stranits . '</p>
        </div>';
}
add_shortcode('statistika', 'statistika_sayta');

// Шорткод [privetstvie] - приветствие с датой
function privetstvie() {
    $data = date('d.m.Y');
    return '<div style="background: #e8f5e9; padding: 15px; border-radius: 8px; text-align: center; border: 1px solid #4CAF50;">
        🐾 Добро пожаловать в наш зоомагазин!<br>
        📅 Сегодня ' . $data . '
        </div>';
}
add_shortcode('privetstvie', 'privetstvie');



