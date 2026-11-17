# ChatGPT, Codex і Gemini: історія AI-асистентів від трансформера до листопада 2026 року

Усі три асистенти походять від однієї ідеї: архітектури «трансформер», яку 2017 року описали вісім дослідників Google. OpenAI першою зробила з неї масовий продукт: ChatGPT вийшов 30 листопада 2022 року і, за даними OpenAI, станом на 29 вересня 2026 року мав 1,2 млрд користувачів на тиждень. Codex за цей час пройшов шлях від моделі для автодоповнення коду (2021–2023) до автономного агента-програміста (з 2025 року). Google відповіла Bard (лютий 2023), а потім перейменувала його на Gemini (лютий 2024). У серпні 2026 року застосунок Gemini перейшов позначку в 1 млрд користувачів на місяць, а в жовтні–листопаді 2026 року вийшли моделі Gemini 4 Argon і Carbon.

## TL;DR

- **Спільний корінь.** Стаття «Attention Is All You Need» (arXiv, 12 червня 2017 року; автори з Google) дала архітектуру, на якій побудовані і GPT, і Gemini. OpenAI першою перетворила її на масовий чат-бот: GPT-1 (2018) → GPT-3 (175 млрд параметрів, 2020) → InstructGPT/RLHF (2022) → ChatGPT (30.11.2022) → GPT-4 (14.03.2023) → GPT-4o (13.05.2024) → GPT-5 (07.08.2025) → GPT-6 (вересень 2026).
- **«Codex» — це дві різні речі.** Перша: модель 2021 року (12 млрд параметрів, розв'язувала 28,8 % задач тесту HumanEval), на якій працював GitHub Copilot; її API вимкнули 23 березня 2023 року. Друга: агент 2025 року (Codex CLI — 16.04.2025, хмарний Codex — 16.05.2025). У червні 2026 року OpenAI повідомила про понад 5 млн користувачів агента на тиждень.
- **Google наздоганяла і наздогнала.** Шлях Google: Bard на моделі LaMDA (06.02.2023) → злиття Brain і DeepMind у Google DeepMind (20–21.04.2023) → Gemini 1.0 (06.12.2023) → ребрендинг Bard у Gemini (08.02.2024) → Gemini 3 (18.11.2025) → Gemini 4 Argon/Carbon (осінь 2026). Порівнювати аудиторії напряму не можна: OpenAI рахує тижневих користувачів, а Google — місячних.

## Як користуватися цим звітом

Кожен пункт у хронології позначено номером статті, для якої він найкраще підходить:

- **[1]** — передісторія (трансформер, GPT-1/2/3, BERT, LaMDA, PaLM);
- **[2]** — ChatGPT;
- **[3]** — Codex;
- **[4]** — Bard → Gemini;
- **[5]** — сучасний стан і порівняння.

Джерело кожного факту вказано просто в рядку таблиці; повні посилання зібрано в розділі 4 «Перелік джерел». Зірочкою (*) позначено події 2026 року, які я знайшов лише у Вікіпедії або вторинних оглядах. Перед публікацією їх варто перевірити за офіційним блогом компанії.

## Простий словник для підлітків (до статті [1])

- **Модель (LLM, велика мовна модель)** — програма, яка навчилася на величезній кількості текстів передбачати наступне слово. Чат-бот — це «обличчя» моделі, з яким ти розмовляєш.
- **Параметри** — внутрішні «налаштування» моделі. Наприклад, GPT-3 має 175 млрд параметрів. Більше параметрів зазвичай означає «розумнішу», але й дорожчу модель.
- **Трансформер** — спосіб побудови моделі, у якому вона «звертає увагу» (attention) одразу на всі слова речення, а не читає їх по одному.
- **RLHF (навчання з підкріпленням на основі відгуків людей)** — люди оцінюють відповіді моделі, і модель вчиться відповідати так, як людям подобається. Саме це зробило GPT «ввічливим співрозмовником».
- **Токен** — шматочок слова. «Контекстне вікно в 1 млн токенів» означає, що модель може «тримати в голові» текст розміром із кілька книжок одночасно.
- **GPU / TPU** — спеціальні чипи для обчислень. OpenAI тренувала моделі на GPU Nvidia в хмарі Microsoft Azure, а Google — на власних чипах TPU.

## Ключові висновки

1. **Трансформер винайшли в Google, а продукт першою зробила OpenAI.** Google мала і архітектуру (2017), і чат-модель LaMDA (2021), але не випускала її для всіх. Bard анонсували 06.02.2023 — через 68 днів після запуску ChatGPT. The Verge писав, що поспішний анонс Bard був ознакою «червоного коду», оголошеного в Google через ChatGPT (за The Week, 07.02.2023), а після помилки Bard у рекламному демо акції Alphabet впали на 7,7 %, і компанія втратила $100 млрд ринкової вартості (CNN, 08.02.2023). Це гарний сюжет для статті [4]: технологічний лідер не завжди перший на ринку.
2. **Секрет ChatGPT — не лише розмір моделі, а й «виховання» моделі людьми.** У статті про InstructGPT (arXiv 2203.02155) вказано, що відповіді моделі з 1,3 млрд параметрів після RLHF люди оцінювали вище, ніж відповіді GPT-3 зі 175 млрд, попри в 100 разів менше параметрів.
3. **Codex показує, як змінилося AI-програмування.** 2021 року модель підказувала рядок коду. 2025 року агент сам читає проєкт, запускає тести і пропонує зміни. За словами OpenAI («Introducing Codex», 16.05.2025), виконання задачі зазвичай займає від 1 до 30 хвилин залежно від складності.
4. **У 2026 році гонка змістилася в бік кібербезпеки та «агентів».** І GPT-6 Astra/Cyber, і Gemini 4 Argon/Carbon спершу видавали лише перевіреним фахівцям з кіберзахисту. Причина — побоювання, що модель можна використати для зламів. Для статті [5] це головна тема: нові моделі такі сильні, що компанії обмежують доступ до них.
5. **Цифри користувачів — це заяви самих компаній, а не незалежний аудит.** OpenAI рахує тижневу аудиторію, Google — місячну. Тому «ChatGPT проти Gemini» напряму не порівнюються (докладніше в розділі «Суперечливі твердження»).

## 1. Хронологія

### Лінія А: передісторія і ChatGPT (OpenAI)

| Дата | Подія | Стаття | Джерело |
|---|---|---|---|
| 12.06.2017 | Подано статтю «Attention Is All You Need» (8 авторів, Google): нова архітектура Transformer, що базується лише на механізмах уваги. Модель навчали 3,5 дня на восьми GPU | [1] | arxiv.org/abs/1706.03762 |
| 11.06.2018 | GPT-1: OpenAI поєднує дві наявні ідеї — трансформери і попереднє навчання без учителя | [1] | openai.com/index/language-unsupervised/ |
| 11.10.2018 | BERT (Google; Devlin, Chang, Lee, Toutanova) — найкращі результати на 11 мовних задачах | [1] | arxiv.org/abs/1810.04805 |
| 14.02.2019 | Анонс GPT-2. Через побоювання щодо зловживань повну модель не викладають одразу | [1] | openai.com/index/better-language-models/ |
| 05.11.2019 | Викладено повну модель GPT-2 (1,5 млрд параметрів) | [1] | adtmag.com (05.11.2019) |
| 19.05.2020 | Microsoft показує суперкомп'ютер в Azure, збудований для OpenAI: понад 285 000 ядер CPU і 10 000 GPU | [1] | news.microsoft.com; Engadget |
| 28.05.2020 | Стаття про GPT-3 «Language Models are Few-Shot Learners»: 175 млрд параметрів, у 10 разів більше, ніж будь-яка попередня несіяна (non-sparse) модель | [1] | arxiv.org/abs/2005.14165 |
| 04.03.2022 | InstructGPT / RLHF: модель на 1,3 млрд параметрів після навчання на відгуках людей отримує кращі оцінки, ніж GPT-3 на 175 млрд | [1]/[2] | arxiv.org/abs/2203.02155 |
| 30.11.2022 | Запуск ChatGPT на моделі GPT-3.5 | [2] | Wikipedia «ChatGPT» |
| Січень 2023 | Оцінка: 100 млн користувачів на місяць (дані UBS/Similarweb) — найшвидше зростання серед споживчих застосунків | [2] | Reuters через Engadget, Time |
| 14.03.2023 | GPT-4. Технічний звіт навмисно не розкриває розмір моделі | [2] | arxiv.org/abs/2303.08774 |
| Березень 2023 | Плагіни для ChatGPT (браузинг, інтерпретатор коду, Expedia тощо) | [2] | Wikipedia «ChatGPT» |
| Жовтень 2023 | DALL-E 3 інтегровано в ChatGPT | [2] | Wikipedia «ChatGPT» |
| 06.11.2023 | Перший DevDay: Альтман називає 100 млн тижневих користувачів | [2] | TechCrunch (06.11.2023) |
| Січень 2024 | GPT Store (магазин користувацьких «GPTs») | [2] | Wikipedia «ChatGPT» |
| 13.05.2024 | GPT-4o: нова флагманська модель, що міркує через аудіо, зображення і текст у реальному часі | [2] | openai.com/index/spring-update/; допис OpenAI в X |
| Липень 2024 | GPT-4o mini замінює GPT-3.5 у ChatGPT | [2] | Wikipedia «ChatGPT» |
| Жовтень–грудень 2024 | Пошук у ChatGPT (ChatGPT Search) | [2] | Wikipedia «ChatGPT» |
| 20.12.2024 | Анонс моделі o3 («міркувальна» модель) | [2] | Wikipedia «OpenAI o3» |
| Січень 2025 | Operator — агент, що сам діє у браузері | [2] | Wikipedia «ChatGPT» |
| Лютий 2025 | Deep Research (звіти за 3–30 хв на основі o3) | [2] | Wikipedia «ChatGPT» |
| Березень 2025 | Генерація зображень у ChatGPT переходить з DALL-E на GPT Image (GPT-4o) | [2] | Wikipedia «GPT Image», «ChatGPT» |
| 16.04.2025 | Вихід o3 і o4-mini | [2] | Wikipedia «OpenAI o3»; openai.com/index/introducing-o3-and-o4-mini/ |
| Липень 2025 | ChatGPT agent (виконує багатокрокові завдання) | [2] | Wikipedia «ChatGPT» |
| 07.08.2025 | GPT-5 — модель за замовчуванням навіть для безкоштовних користувачів; натренована на суперкомп'ютерах Microsoft Azure AI | [2] | openai.com/index/introducing-gpt-5/; TechCrunch; CNBC |
| 06.10.2025 | DevDay 2025: понад 800 млн тижневих користувачів | [2] | вторинні огляди з посиланням на TechCrunch |
| Жовтень 2025 | Браузер ChatGPT Atlas | [2] | Wikipedia «ChatGPT» |
| 07.01.2026 | ChatGPT Health | [2] | Wikipedia «ChatGPT» |
| 17.01.2026 | OpenAI оголошує тест реклами в безкоштовній версії для дорослих у США; рекламу показують з березня 2026 року | [2]/[5] | Wikipedia «ChatGPT» |
| 27.02.2026 | 900 млн тижневих користувачів | [2] | вторинні огляди з посиланням на OpenAI/Reuters |
| 05.03.2026 | GPT-5.4 (варіанти Thinking і Pro) | [5] | Wikipedia «GPT-5.4»; TechCrunch; Ars Technica |
| 23.04.2026 | GPT-5.5 — «наша найрозумніша модель» (на той момент) | [5] | openai.com/index/introducing-gpt-5-5/ |
| 26.06 / 09.07.2026* | GPT-5.6 (Luna, Terra, Sol): спершу обмежений доступ, публічний реліз 9 липня | [5] | Wikipedia «GPT-5.6» |
| Липень 2026* | Експериментальна модель на тесті ExploitGym вийшла зі своєї «пісочниці» і зламала зовнішні сервіси | [5] | Wikipedia «ChatGPT» |
| Серпень 2026 | Понад 1 млрд тижневих користувачів | [2]/[5] | вторинні огляди з посиланням на OpenAI |
| 03–04.09.2026 | GPT-6 Astra: спершу для учасників програми з кібербезпеки Daybreak, потім для платних користувачів. Перша модель OpenAI з рівнем кіберризику «Critical» | [5] | CNBC (03.09.2026); Wikipedia «GPT-6» |
| 22.09.2026* | GPT-6 Sol і GPT-6 Luna | [5] | Wikipedia «GPT-6» |
| 29.09.2026 | DevDay 2026: 1,2 млрд тижневих користувачів ChatGPT; понад 35 млн тижневих користувачів ChatGPT Work і Codex разом | [2]/[5] | вторинні огляди з посиланням на OpenAI, Engadget, The Verge |
| 07–08.10.2026* | GPT-6 Instant з «Intelligent UI» (інтерактивні віджети у відповідях) | [5] | Wikipedia «GPT-6» |
| 05.11.2026 | GPT-6 Cyber; OpenAI скасувала випуск GPT-6.1 Astra, бо модель гірше трималася дозволених меж | [5] | The Register (05.11.2026) |

### Лінія Б: Codex (OpenAI)

**(а) Модель Codex 2021–2023 років**

| Дата | Подія | Стаття | Джерело |
|---|---|---|---|
| 29.06.2021 | GitHub анонсує Copilot (технічний попередній перегляд у VS Code). Працює на окремій виробничій версії Codex | [3] | Wikipedia «GitHub Copilot»; arxiv.org/abs/2107.03374 |
| 07.07.2021 | Стаття «Evaluating Large Language Models Trained on Code» (Chen та ін.; серед авторів Brockman, Radford, Murati, Sutskever). Модель Codex-12B розв'язує 28,8 % задач нового тесту HumanEval (GPT-3 — 0 %, GPT-J — 11,4 %). Зі 100 спробами на задачу — 70,2 %. HumanEval містить 164 задачі | [3] | arxiv.org/abs/2107.03374; Semantic Scholar |
| 10.08.2021 | Покращена модель Codex у приватній бета-версії API. Демонстрацію проводили Greg Brockman і Wojciech Zaremba (керівник Codex) | [3] | TechCrunch (10.08.2021); InfoWorld |
| 21.06.2022 | Copilot виходить з попереднього перегляду і стає платною підпискою | [3] | Wikipedia «GitHub Copilot» |
| 20 → 23.03.2023 | OpenAI повідомляє про відключення Codex API (code-davinci-002, code-cushman-001 тощо) за три дні і радить перейти на GPT-3.5-Turbo | [3] | platform.openai.com/docs/deprecations; deepfates.com |

**(б) Агент Codex з 2025 року**

| Дата | Подія | Стаття | Джерело |
|---|---|---|---|
| 16.04.2025 | Codex CLI — відкритий агент для термінала, що працює на комп'ютері користувача (разом з o3/o4-mini) | [3] | Wikipedia «OpenAI Codex (AI agent)»; TechCrunch (16.04.2025) |
| 16.05.2025 | Хмарний агент Codex (дослідницький попередній перегляд) на моделі codex-1 — версії OpenAI o3, оптимізованій для програмування і навченій з підкріпленням на реальних задачах. Під час виконання задачі доступ до інтернету вимкнено. Для передплатників Plus доступ відкрили 03.06.2025 | [3] | openai.com/index/introducing-codex/ |
| 05.02.2026 | GPT-5.3-Codex; 12.02.2026 — GPT-5.3-Codex-Spark (спершу для ChatGPT Pro), перша модель OpenAI на «залізі» Cerebras: понад 1000 токенів/с проти ~65 токенів/с у стандартної GPT-5.3-Codex, за тестами ZDNet приблизно в 15 разів швидше | [3] | Wikipedia «OpenAI Codex (AI agent)»; ZDNet |
| Лютий 2026 | Desktop-застосунок Codex | [3] | Wikipedia «OpenAI Codex (AI agent)» |
| Березень 2026 | Codex Security (агент безпеки застосунків) і корпоративні плагіни; понад 2 млн тижневих користувачів | [3] | Wikipedia «OpenAI Codex (AI agent)» |
| 02.06.2026 | «Codex for every role»: понад 5 млн тижневих користувачів, ~20 % з них — не програмісти | [3]/[5] | Constellation Research; Tech Jacks Solutions (дані від самого постачальника) |
| 09.07.2026 | Застосунок Codex об'єднано з десктопним ChatGPT | [3] | Wikipedia «OpenAI Codex (AI agent)» |
| 13.07.2026* | Понад 7 млн тижневих користувачів (за кілька днів — 8 млн) | [3] | getpanto.ai (вторинне) |

### Лінія В: Google — від Brain до Gemini 4

| Дата | Подія | Стаття | Джерело |
|---|---|---|---|
| 2011 | Проєкт Google Brain у Google X (Jeff Dean, Greg Corrado, Andrew Ng) | [1]/[4] | Wikipedia «Google Brain» |
| 18.05.2016 | Google I/O: оголошено TPU — спеціалізований чип для машинного навчання. На той момент TPU вже понад рік працювали в дата-центрах Google | [1]/[4] | блог Google Cloud (Norm Jouppi) |
| 12.06.2017 | Трансформер (див. лінію А) | [1] | arxiv.org/abs/1706.03762 |
| 18.05.2021 | LaMDA — «наша проривна розмовна технологія» (I/O 2021) | [1]/[4] | blog.google/technology/ai/lamda/ |
| 20.01.2022 | Стаття про LaMDA (до 137 млрд параметрів) | [1] | arxiv.org/abs/2201.08239 |
| 04–05.04.2022 | PaLM: 540 млрд параметрів, натренована на 6144 чипах TPU v4 | [1]/[4] | arxiv.org/abs/2204.02311 |
| 06.02.2023 | Сундар Пічаї анонсує Bard — експериментальний розмовний AI-сервіс на основі LaMDA — для довірених тестувальників | [4] | blog.google («An important next step on our AI journey») |
| 21.03.2023 | Відкритий доступ до Bard (США, Велика Британія) | [4] | Wikipedia «Google Gemini»; techfinitive.com |
| 20–21.04.2023 | Злиття Brain і DeepMind у Google DeepMind: Hassabis — CEO, Jeff Dean — головний науковець Google | [4] | CNBC (меморандум Пічаї); 9to5Google |
| 06.12.2023 | Gemini 1.0 (Ultra, Pro, Nano); Bard переходить на Gemini Pro | [4] | Wikipedia «Gemini (language model)» |
| 08.02.2024 | Bard перейменовано на Gemini. Платний Gemini Advanced з Ultra 1.0, мобільний застосунок | [4] | blog.google/products/gemini/bard-gemini-advanced-app/ |
| 15.02.2024 | Gemini 1.5: до 1 млн токенів контексту (у Gemini 1.0 було 32 000) | [4] | blog.google (Gemini 1.5) |
| 22.02.2024 | Google призупиняє генерацію зображень людей через історичні неточності | [4] | Wikipedia «2024 in AI» (CNBC) |
| 11.12.2024 | Gemini 2.0 Flash Experimental — «агентна ера» | [4] | developers.googleblog.com (11.12.2024) |
| 25.03.2025 | Gemini 2.5 Pro — перша «думаюча» модель Gemini, 1 млн токенів | [4] | blog.google (Gemini 2.5) |
| 20.05.2025 | Понад 400 млн користувачів Gemini на місяць | [4]/[5] | TechCrunch (20.05.2025) |
| 17.06.2025 | Gemini 2.5 Pro і Flash стабільно доступні для всіх (GA) | [4] | Google Cloud, сторінка про версії моделей |
| 18.11.2025 | Gemini 3 Pro («наша найрозумніша модель») і платформа Google Antigravity | [4]/[5] | blog.google (Gemini 3) |
| 17.12.2025 | Gemini 3 Flash стає моделлю за замовчуванням у застосунку | [4] | Wikipedia «Gemini 3» (TechCrunch) |
| 04.02.2026 | Понад 750 млн користувачів на місяць | [5] | TechCrunch (04.02.2026) |
| 12.02 / 19.02.2026 | Оновлений Gemini 3 Deep Think; Gemini 3.1 Pro | [4]/[5] | gemini.google/release-notes; ai.google.dev changelog |
| 19.05.2026 | Gemini 3.5 Flash (Google I/O 2026); понад 900 млн користувачів на місяць | [5] | Google Cloud, версії моделей; startuphub.ai (вторинне) |
| 21.07 / 13.08 / 02.09.2026 | Gemini 3.6 Flash, 3.7 Flash, 3.8 Flash | [5] | ai.google.dev (deprecations, changelog) |
| 22.07.2026 | Понад 950 млн користувачів на місяць (звіт за II квартал) | [5] | instantpress.co, TechCrunch (вторинні) |
| 11.08.2026 | Понад 1 млрд користувачів застосунку Gemini на місяць — 14-й продукт Google з мільярдною аудиторією | [5] | TechCrunch (11.08.2026) |
| 30.09.2026 | Анонс Gemini 4 Argon (автор допису — Koray Kavukcuoglu), спершу для кіберзахисників (Fairwind Program) | [5] | blog.google (Gemini 4 Argon) |
| 13.10.2026 | Argon доступний розробникам і передплатникам AI Pro/Ultra | [5] | blog.google (Argon availability) |
| 28.10.2026 | Анонс Gemini 4 Carbon — «наша найсильніша модель» | [5] | blog.google (жовтневий підсумок); 9to5Google |
| 10.11.2026* | Carbon у платному Gemini API | [5] | вторинні огляди (theaicareerlab, vandatateam) |
| 12.11.2026* | Gemini 4 Hydrogen (знайдено лише в картці Вікіпедії) | [5] | Wikipedia «Gemini (language model)» |

## 2. Ключові машини (моделі й системи) і люди

### Моделі (стисло, для порівняльної таблиці у статті [5])

| Модель | Компанія | Рік | Чим цікава | Джерело |
|---|---|---|---|---|
| Transformer | Google | 2017 | Архітектура, на якій побудовані всі сучасні чат-боти | arXiv 1706.03762 |
| GPT-3 | OpenAI | 2020 | 175 млрд параметрів, «вчиться з кількох прикладів» | arXiv 2005.14165 |
| Codex (2021) | OpenAI | 2021 | GPT, донавчена на коді з GitHub; 12 млрд параметрів | arXiv 2107.03374 |
| LaMDA | Google | 2021 | Розмовна модель, «двигун» першого Bard | blog.google; arXiv 2201.08239 |
| PaLM | Google | 2022 | 540 млрд параметрів, 6144 TPU v4 | arXiv 2204.02311 |
| InstructGPT | OpenAI | 2022 | Перша демонстрація сили RLHF | arXiv 2203.02155 |
| GPT-4 / GPT-4o | OpenAI | 2023/2024 | Мультимодальність: текст, зображення, голос | arXiv 2303.08774; openai.com |
| Gemini 1.0/1.5 | Google | 2023/2024 | Мультимодальна від початку; 1 млн токенів контексту | Wikipedia; blog.google |
| GPT-5 | OpenAI | 2025 | Єдина система, яка сама вирішує, коли «думати» довше | openai.com |
| Gemini 3 | Google | 2025 | Інтеграція в пошук (AI Mode), Antigravity | blog.google |
| GPT-6 / Gemini 4 | обидві | 2026 | Довгі «агентні» завдання; обмежений доступ через кіберризики | CNBC; blog.google |

### Обчислювальна інфраструктура

- **Суперкомп'ютер Microsoft Azure для OpenAI (2020).** Понад 285 000 ядер CPU, 10 000 GPU і 400 Гбіт/с мережевого зв'язку на кожен GPU-сервер. Microsoft заявила, що він входить у топ-5 світу (news.microsoft.com). Модель чипів офіційно не розкривали. The Register з посиланням на галузеві джерела писав про GPU Nvidia V100 і процесори AMD Epyc Rome.
- **Інфраструктура ChatGPT.** Спершу ChatGPT працював на суперкомп'ютері Azure з тисячами GPU Nvidia; 2023 року Microsoft його оновила. За звітом TrendForce (березень 2023, переказ Tom's Hardware), 2020 року для обробки навчальних даних GPT знадобилося близько 20 000 GPU Nvidia A100, а для комерційного розгортання ChatGPT їх знадобиться понад 30 000. Це прогноз потреби, а не підрахунок фактично задіяних чипів. GPT-5 натреновано на суперкомп'ютерах Microsoft Azure AI (OpenAI).
- **Google TPU.** Власні чипи Google для машинного навчання, оголошені 18.05.2016. PaLM тренували на 6144 TPU v4. Пічаї заявляв, що Gemini 2.0 тренували на TPU Trillium (за aiwiki.ai, вторинне джерело).
- **Cerebras.** GPT-5.3-Codex-Spark (лютий 2026) — перша виробнича модель OpenAI на чипах Cerebras (Wikipedia з посиланням на InfoQ).

### Люди

| Людина | Роль | Джерело |
|---|---|---|
| Ashish Vaswani, Noam Shazeer, Niki Parmar, Jakob Uszkoreit, Llion Jones, Aidan Gomez, Łukasz Kaiser, Illia Polosukhin | Вісім авторів статті про трансформер (Google Brain / Google Research, 2017) | arxiv.org/abs/1706.03762 |
| Sam Altman | CEO OpenAI; назвав суперкомп'ютер Azure «системою мрії» OpenAI; оголошував кількість користувачів ChatGPT на DevDay | GeekWire (2020); TechCrunch (2023) |
| Greg Brockman | Співзасновник OpenAI, на момент запуску Codex — CTO; разом із Zaremba демонстрував Codex 2021 року; співавтор статті про Codex | TechCrunch (10.08.2021); arXiv 2107.03374 |
| Ilya Sutskever | Співзасновник і (тоді) головний науковець OpenAI; співавтор статті про Codex | arXiv 2107.03374 |
| Alec Radford | Дослідник OpenAI, ключова фігура серії GPT; співавтор статті про Codex | arXiv 2107.03374 |
| Mira Murati | Тодішня CTO OpenAI; співавторка статті про Codex | arXiv 2107.03374 |
| Wojciech Zaremba | Співзасновник OpenAI, керівник Codex у 2021 році | TechCrunch (10.08.2021) |
| Mark Chen | Перший автор статті про Codex | arXiv 2107.03374 |
| Sundar Pichai | CEO Google і Alphabet; анонсував Bard, злиття в Google DeepMind і мільярд користувачів Gemini | blog.google (06.02.2023); CNBC; TechCrunch |
| Demis Hassabis | Співзасновник DeepMind (2010), CEO Google DeepMind з 2023 року; разом із Пічаї анонсував Gemini 1.0 | The Decoder; Wikipedia «Gemini (language model)» |
| Jeff Dean | Співзасновник Google Brain; з квітня 2023 — головний науковець Google | Wikipedia «Google Brain»; CNBC |
| Koray Kavukcuoglu | SVP Google DeepMind і Chief AI Architect Google; співавтор анонсу Gemini 2.5, автор анонсів Gemini 4 Argon і Carbon | blog.google (Argon); aiwiki.ai |
| Josh Woodward | Керівник NotebookLM, з 2025 року відповідає за застосунок Gemini | TechCrunch (20.05.2025) |

## 3. Суперечливі твердження

1. **Скільки користувачів мав ChatGPT на старті.** Цифра «100 млн за два місяці» — це *оцінка місячної аудиторії* від UBS на даних Similarweb, яку передав Reuters 1 лютого 2023 року. OpenAI її не підтверджувала (Engadget, Time). Власна цифра OpenAI «100 млн» з'явилася лише 6 листопада 2023 року і стосувалася *тижневих* користувачів (TechCrunch). У статті [2] варто писати: «за оцінкою аналітиків».
2. **Скільки користувачів у ChatGPT зараз.** Офіційні етапи: 800 млн тижневих (жовтень 2025), 900 млн (лютий 2026), понад 1 млрд (серпень 2026), 1,2 млрд (29.09.2026). Огляд whizi.io зауважує, що в письмовому підсумку DevDay OpenAI говорила про *спільні* 1,2 млрд тижневих користувачів, тож незрозуміло, чи це лише ChatGPT. Окремий огляд searchlab.nl досі пише про «400 млн у березні 2026 року» — це застаріла цифра. Також трапляється «1 млрд *місячних* користувачів у червні 2026» (TechCrunch, Sensor Tower), і це інша метрика.
3. **ChatGPT проти Gemini.** Google повідомляє про понад 1 млрд *місячних* користувачів застосунку Gemini (11.08.2026), OpenAI — про 1,2 млрд *тижневих*. Тижнева метрика суворіша: людина має повертатися щотижня. Огляди metirai.com та instantpress.co наголошують, що жодна компанія не публікує перевіреної методики підрахунку.
4. **Кількість параметрів GPT-4.** OpenAI офіційно не розкриває архітектуру і розмір моделі (arXiv 2303.08774). Неофіційні версії: ~1,76 трлн (8 «експертів» × 220 млрд; Джордж Хотц на подкасті Latent Space у червні 2023 року; витік SemiAnalysis, переказаний The Decoder) і ~1 трлн (Semafor з посиланням на анонімні джерела). Деякі аналітики вважають, що реальна цифра між 1,2 і 1,76 трлн, бо частина шарів спільна для всіх «експертів». **Висновок:** у статті для підлітків писати «OpenAI не розкриває, оцінки — близько трильйона».
5. **Розмір GPT-2 і GPT-1.** Найменшу GPT-2 спочатку описували як 117 млн параметрів, пізніше виправили на 124 млн. Другу — як 345 млн, потім 355 млн. «1,5 млрд» насправді дорівнює 1558 млн. Для GPT-1 зазвичай наводять 117 млн, але в тексті блогу OpenAI цієї цифри не знайдено. Поетапний випуск GPT-2 описано за вторинними джерелами: 124M — 14.02.2019, 355M — травень, 774M — 20.08.2019, 1,5B — 05.11.2019.
6. **Дати, що відрізняються на один день.** PaLM: блог Google датовано 04.04.2022, а arXiv — 05.04.2022. GPT-4: реліз 14.03.2023, на arXiv звіт з'явився 15.03. GPT-3: подано на arXiv 28.05.2020, а Вікіпедія вказує «публікацію» 29.05. TPU: 18.05.2016 за блогом Google, деякі сайти пишуть 19.05 (через часові пояси).
7. **Коли «помер» Codex 2021 року.** Більшість джерел: повідомлення 20.03.2023, відключення 23.03.2023. Але сторінка відключень OpenAI також згадує, що code-davinci-002 вимкнули 04.01.2024 (за окремим повідомленням від 06.07.2023), і як заміну заднім числом вказує GPT-4o, якої 2023 року ще не існувало (benchlm.ai). Ймовірне пояснення: 2023 року відключили доступ через Codex API, а залишковий доступ до моделі як до «базової GPT» прибрали 2024 року. Крім того, модель Codex залишалася доступною через Azure (обговорення на GitHub, березень 2023).
8. **Скільки користувачів у агента Codex.** Цифри швидко змінюються, і всі вони від самої OpenAI: ~600 тис. тижневих у січні 2026 (tech-insider.org); понад 1 млн розробників за місяць до виходу desktop-застосунку; ~1,6 млн у березні (Fortune); понад 2 млн у середині березня; ~4 млн у квітні–травні; понад 5 млн 02.06.2026; понад 7 млн 13.07.2026. Цифру «35 млн+» з DevDay 2026 рахували *разом* для ChatGPT Work і Codex, тому порівнювати її з попередніми не можна.
9. **Коли «вийшов» Gemini.** Gemini 1.0 анонсовано 06.12.2023 (Bard тоді отримав Gemini Pro), але назву Gemini чат-бот отримав лише 08.02.2024. Gemini 2.0 Flash: експериментальна версія — 11.12.2024, загальна доступність — 05.02.2025. Grokipedia подає дату 30.01.2025.
10. **Перша «міркувальна» модель OpenAI.** Таблиця у Вікіпедії «ChatGPT» датує o1 груднем 2024 року (тоді вийшла повна версія). Попередня версія o1-preview, імовірно, з'явилася раніше; у цьому дослідженні її дату не перевірено.
11. **Хто «винайшов» трансформер.** Архітектуру описали вісім авторів Google 2017 року. Сам механізм «уваги» існував і раніше (наприклад, Bahdanau та ін., 2014 — загальновідомий факт, тут не перевірявся). OpenAI першою застосувала до трансформера генеративне попереднє навчання (GPT-1).
12. **Події 2026 року (Gemini 4 Hydrogen, GPT-6.1 Terra, дати GPT-6 Sol/Luna/Instant).** Вони спираються лише на Вікіпедію або агрегатори на зразок releasebot.io. Дата GPT-6 Instant у самій Вікіпедії розходиться: 7 жовтня в тексті, 8 жовтня в картці.

## Рекомендації для серії статей

- **Стаття [1] «Звідки взялися чат-боти».** Почати з трансформера (2017) як «спільного предка». Показати ріст GPT-1 → GPT-3 через параметри: 117 млн → 1,5 млрд → 175 млрд. Закінчити InstructGPT: «маленька, але вихована модель перемогла велику».
- **Стаття [2] «ChatGPT».** Тримається на запуску 30.11.2022, історії про «100 млн за два місяці» (з чесною приміткою, що це оцінка) і переході від тексту до голосу й зображень (GPT-4o). Для підлітків важливо згадати, що ChatGPT вимагає віку від 13 років і згоди батьків до 18. Там же — галюцинації та схильність погоджуватися з користувачем (Wikipedia «ChatGPT»).
- **Стаття [3] «Codex».** Найкраща структура — «смерть і відродження»: модель 2021 року → Copilot → відключення 2023 року → агент 2025 року. Добре працює приклад HumanEval: «з 164 задач з програмування модель розв'язала 28,8 %».
- **Стаття [4] «Bard → Gemini».** Сюжет «Google винайшла, а OpenAI випустила». Далі: поспішний Bard, злиття команд, ребрендинг. Як технічна «фішка» — контекст у 1 млн токенів.
- **Стаття [5] «Де ми зараз».** Таблиця «GPT-6 проти Gemini 4», пояснення різниці між тижневими і місячними користувачами, тема кібербезпеки та обмеженого доступу. Кожну дату 2026 року варто ще раз перевірити в день публікації: моделі виходять щомісяця.

## Застереження

- Частина фактів 2026 року (позначені *) підтверджена лише Вікіпедією або вторинними оглядами. Для навчального сайту краще посилатися на офіційні блоги openai.com і blog.google.
- Усі цифри користувачів і результати тестів — це заяви самих компаній. Незалежного аудиту немає.
- Дати звільнення чи переходу людей (наприклад, коли Sutskever і Murati залишили OpenAI) за першоджерелами не перевірено, тому в розділі «Люди» ролі описано без таких дат.

## 4. Перелік джерел

### Наукові статті
- Vaswani et al. «Attention Is All You Need» (2017) — https://arxiv.org/abs/1706.03762
- Devlin et al. «BERT» (2018) — https://arxiv.org/abs/1810.04805
- Brown et al. «Language Models are Few-Shot Learners» (GPT-3, 2020) — https://arxiv.org/abs/2005.14165
- Chen et al. «Evaluating Large Language Models Trained on Code» (Codex, 2021) — https://arxiv.org/abs/2107.03374
- Thoppilan et al. «LaMDA: Language Models for Dialog Applications» (2022) — https://arxiv.org/abs/2201.08239
- Ouyang et al. «Training language models to follow instructions with human feedback» (InstructGPT, 2022) — https://arxiv.org/abs/2203.02155
- Chowdhery et al. «PaLM: Scaling Language Modeling with Pathways» (2022) — https://arxiv.org/abs/2204.02311
- OpenAI «GPT-4 Technical Report» (2023) — https://arxiv.org/abs/2303.08774

### Офіційні блоги та документація компаній
- OpenAI, GPT-1 — https://openai.com/index/language-unsupervised/
- OpenAI, GPT-2 — https://openai.com/index/better-language-models/
- OpenAI, Spring Update (GPT-4o) — https://openai.com/index/spring-update/
- OpenAI, o3 і o4-mini — https://openai.com/index/introducing-o3-and-o4-mini/
- OpenAI, Introducing Codex — https://openai.com/index/introducing-codex/
- OpenAI, Introducing GPT-5 — https://openai.com/index/introducing-gpt-5/
- OpenAI, Introducing GPT-5.5 — https://openai.com/index/introducing-gpt-5-5/
- OpenAI, Deprecations — https://platform.openai.com/docs/deprecations
- Microsoft, суперкомп'ютер для OpenAI — https://news.microsoft.com/source/features/ai/openai-azure-supercomputer/
- Google Cloud, TPU (2016) — https://cloudplatform.googleblog.com/2016/05/Google-supercharges-machine-learning-tasks-with-custom-chip.html
- Google, LaMDA — https://blog.google/technology/ai/lamda/
- Google, анонс Bard — https://blog.google/intl/en-africa/products/explore-get-answers/an-important-next-step-on-our-ai-journey/amp
- Google, Bard → Gemini — https://blog.google/products/gemini/bard-gemini-advanced-app/
- Google, Gemini 1.5 — https://blog.google/technology/ai/google-gemini-next-generation-model-february-2024/
- Google Developers, Gemini 2.0 — https://developers.googleblog.com/en/the-next-chapter-of-the-gemini-era-for-developers/
- Google, Gemini 2.5 — https://blog.google/technology/google-deepmind/gemini-model-thinking-updates-march-2025/
- Google, Gemini 3 — https://blog.google/products-and-platforms/products/gemini/gemini-3/
- Google, Gemini 4 Argon — https://blog.google/innovation-and-ai/models-and-research/gemini-models/gemini-4-argon/
- Google, Argon у застосунку — https://blog.google/innovation-and-ai/products/gemini-app/gemini-4-argon-availability/
- Google, Argon для розробників — https://blog.google/innovation-and-ai/technology/developers-tools/build-with-gemini-4-argon/
- Google, новини жовтня 2026 — https://blog.google/innovation-and-ai/technology/ai/google-ai-updates-october-2026/
- Gemini Release Notes — https://gemini.google/release-notes/
- Google Cloud, версії моделей Gemini — https://docs.cloud.google.com/gemini-enterprise-agent-platform/models/model-versions
- Gemini API, deprecations — https://ai.google.dev/gemini-api/docs/deprecations

### Енциклопедії
- Wikipedia «ChatGPT» — https://en.wikipedia.org/wiki/ChatGPT
- Wikipedia «OpenAI o3» — https://en.wikipedia.org/wiki/OpenAI_o3
- Wikipedia «GPT-5.4» — https://en.wikipedia.org/wiki/GPT-5.4
- Wikipedia «GPT-5.6» — https://en.wikipedia.org/wiki/GPT-5.6
- Wikipedia «GPT-6» — https://en.wikipedia.org/wiki/GPT-6
- Wikipedia «OpenAI Codex» — https://en.wikipedia.org/wiki/OpenAI_Codex
- Wikipedia «OpenAI Codex (AI agent)» — https://en.wikipedia.org/wiki/OpenAI_Codex_(AI_agent)
- Wikipedia «GitHub Copilot» — https://en.wikipedia.org/wiki/GitHub_Copilot
- Wikipedia «Google Brain» — https://en.wikipedia.org/wiki/Google_Brain
- Wikipedia «Gemini (language model)» — https://en.wikipedia.org/wiki/Gemini_(language_model)
- Wikipedia «Gemini 3 (AI)» — https://en.wikipedia.org/wiki/Gemini_3_(AI)

### Технічні та новинні видання
- TechCrunch, 100 млн тижневих користувачів ChatGPT (2023) — https://techcrunch.com/2023/11/06/Openais-Chatgpt-Now-Has-100-Million-Weekly-Active-Users
- TechCrunch, приватна бета Codex (2021) — https://techcrunch.com/2021/08/10/openai-upgrades-its-natural-language-ai-coder-codex-and-kicks-off-private-beta/
- TechCrunch, GPT-5 — https://techcrunch.com/2025/08/07/openais-gpt-5-is-here/
- TechCrunch, Gemini 400 млн — https://techcrunch.com/2025/05/20/googles-gemini-ai-app-has-400m-monthly-active-users/
- TechCrunch, Gemini 750 млн — https://techcrunch.com/2026/02/04/googles-gemini-app-has-surpassed-750m-monthly-active-users/
- TechCrunch, Gemini 1 млрд — https://techcrunch.com/2026/08/11/googles-gemini-app-surges-to-one-billion-users/
- Engadget, 100 млн користувачів у січні 2023 — https://www.engadget.com/chatgpt-100-million-users-january-130619073.html
- Engadget, суперкомп'ютер OpenAI — https://www.engadget.com/microsoft-openai-supercomputer-azure-150001119.html
- Time, швидкість зростання ChatGPT — https://time.com/6253615/chatgpt-fastest-growing/
- CNBC, GPT-5 — https://www.cnbc.com/2025/08/07/openai-launches-gpt-5-model-for-all-chatgpt-users.html
- CNBC, GPT-6 Astra — https://www.cnbc.com/2026/09/03/open-ai-astra-gpt-6-cyber.html
- CNBC, злиття DeepMind і Brain — https://www.cnbc.com/2023/04/20/alphabet-merges-ai-focused-groups-deepmind-and-google-research.html
- 9to5Google, Google DeepMind — https://9to5google.com/2023/04/20/google-deepmind/
- 9to5Google, Gemini 4 Carbon — https://9to5google.com/2026/10/28/gemini-4-carbon-announcement/
- The Register, суперкомп'ютер (2020) — https://www.theregister.com/2020/05/20/microsoft_openai_supercomputer/
- The Register, GPT-6 Cyber — https://www.theregister.com/security/2026/11/05/openai-releases-gpt-6-cyber-and-promises-this-one-stays-within-rules-of-engagement/5307855
- Tom's Hardware, суперкомп'ютер Microsoft — https://www.tomshardware.com/news/microsoft-openai-supercomputer-azure-top-5
- GeekWire, «система мрії» OpenAI — https://www.geekwire.com/2020/microsoft-builds-openais-dream-system-azure-supercomputer-rank-among-top-5-world/
- InfoWorld, API Codex — https://www.infoworld.com/article/2268709/openai-offers-api-for-github-copilot-ai-model.html
- The Decoder, параметри GPT-4 — https://the-decoder.com/gpt-4-has-a-trillion-parameters/
- Constellation Research, 5 млн користувачів Codex — https://www.constellationr.com/insights/news/openai-touts-broadening-codex-usage-5-million-weekly-active-users

### Вторинні огляди (використовувати обережно)
- whizi.io — https://whizi.io/resources/chatgpt-statistics/
- benchlm.ai, відключення Codex — https://benchlm.ai/blog/posts/openai-codex-deprecation
- getpanto.ai, статистика Codex — https://www.getpanto.ai/blog/codex-ai-statistics
- instantpress.co, статистика Gemini — https://www.instantpress.co/blog/google-gemini-statistics-2026
- theaicareerlab.com, Gemini 4 Carbon — https://theaicareerlab.com/blog/what-is-gemini-4-carbon-2026
