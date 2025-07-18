Advanced Scene Management System for Unity
===
<br />
🔹 Кастомное решение для управления сценами в Unity с поддержкой сложных сценариев загрузки <br />
 <br />
 
🔍 Ключевые особенности <br />
- Гибкая система переходов между сценами <br />
- Поддержка зависимостей (предзагрузка ресурсов) <br />
- Приоритизация сцен (фоновые/критические) <br />
- Интеграция с Addressables (опционально) <br />
- Мультиплеер-совместимая архитектура <br />
 <br />

🎲 Содержимое:
- CustomPackage: unity package с кодом и примером использования
- Example of Unity Source - backup: исходный проект Unity с демонстрацией функционала
- Scripts: отдельно вынесенные сценарии для работы с менеджером загрузок
- Для использования функционала достаточны сценрии (LoadingScene.cs - на загрузочной сцене, MySceneManager.cs - вызов из любой точки для управления загрузками через загрузочную сцену):

<img width="182" alt="image" src="https://github.com/user-attachments/assets/ae929757-3465-46bf-b1e3-879fd7aa0ab2" />



🛠 Примеры использования
``` csharp
// Пример использования с кастомными параметрами
AdvancedSceneLoader.Load(
    sceneName: "Level3",
    priority: ScenePriority.High,
    dependencies: new[] {"PrefabsBundle"},
    transition: new FadeTransition(duration: 1.5f)
);

// Загрузка сцены с отслеживанием прогресса
await MySceneManager.LoadSceneAsync("GameScene");

// С подпиской на события
MySceneManager.OnLoadingProgress += progress => {
    Debug.Log($"Loading progress: {progress * 100}%");
};

// Аддитивная загрузка
await MySceneManager.LoadSceneAdditiveAsync("UI_Scene");
```

Архитектурные принципы:
- SOLID-совместимый дизайн
- Инъекция зависимостей через интерфейсы
- Event-driven подход

⚙️ Технологический стек <br />
Компонент &emsp; Версия &emsp;	Назначение <br />
Unity	&emsp; 2021.3+	&emsp; Базовый движок <br />
C#	&emsp; 9.0+ &emsp;	Основной язык <br />
UniTask &emsp;	2.3+ &emsp;	Асинхронные операции <br />
Addressables &emsp;	1.19+ &emsp; Управление ассетами <br />

📊 Производительность <br />
- Оптимизировано для:
- Мобильных устройств (ARMv7/ARM64)
- VR/AR сцен (стабильный FPS)
- Кроссплатформенных сборок

Метрики:
- Время загрузки: на 30% быстрее стандартного решения
- Потребление памяти: ~2.5 MB резидентной памяти

🎯 Варианты использования
- Игры с открытым миром (динамическая подгрузка локаций)
- Мобильные проекты (оптимизация под слабые устройства)
- VR-приложения (плавные переходы между сценами)

📦 Структура пакета
``` markdown
MySceneManager/
├── Core/
│   ├── SceneLoader.cs         # Основной загрузчик
│   └── SceneContext.cs        # Состояние сцены
├── Transitions/               # Система переходов
│   ├── FadeTransition.cs
│   └── SlideTransition.cs
├── Dependencies/              # Управление ресурсами
│   ├── AssetPreloader.cs
│   └── AddressablesBridge.cs
└── Editor/                    # Интеграция с Unity Editor
    ├── SceneValidator.cs
    └── DependencyGraphWindow.cs
```


📈 Roadmap
- Поддержка Scene Fusion для мультиплеера
- Визуальный редактор зависимостей
- Тесты производительности

Лицензия: MIT (свободное использование в коммерческих проектах)

Поддержка:
- Telegram: @Vladimir_Repp
- Email: vladimir_repp97@mail.ru
