# EasyWoW

# Advanced API

+ <strong>L</strong> - Локальная функция, для её вызова необходимо инициализировать <strong>API</strong>.
+ <strong>G</strong> - Глобальная функция, доступна без инициализации <strong>API</strong>.
+ <strong>bool</strong> - Логический тип переменной = <strong>TRUE</strong> or <strong>FALSE</strong>.
+ <strong>int</strong> - Целочисленное число = от <strong>−2147483648</strong> до  <strong>+2147483647</strong>.
+ <strong>float</strong> - Число с плавающей запятой = от <strong>-3.4028235E+38</strong> до  <strong>+3.4028235E+38</strong>.
+ <strong>string</strong> - Текстовое значение.
+ <strong>table</strong> - Таблица.
+ <strong>void</strong> - Не имеет значения.
+ <strong>...</strong> - Мультиаргумент.
<br><br>

+ Имя функции <strong>Execute</strong> меняется в ижеторе.
+ Имя функции <strong>ExecuteFile</strong> зависит от функции Execute и добавляется префикс File.
+ Имя функции <strong>EasyWoW</strong> меняется в ижеторе.
+ Макрос <strong>/execute</strong> изменяется в зависимости от имени функции <strong>Execute</strong>.

## Системные функции

>L: Сброс афк таймера:
```cpp
(void) ResetAFKTimer();
```
>L: Показать счётчик FPS:
```cpp
(void) ShowFPS(boolean or integer)
```
L: Показать/Скрыть окно программы:
```cpp
(void) EasyWoW(boolean or integer);
```
><b>G:</b> Инициализации локальных API и таблиц:
```cpp
(table) API, ENUMs = EWAPI(); 
/* example:
    /run api = EWAPI() api.ResetAFKTimer();
*/
```

>L: Разблокировка луа для определённого аддона:
```cpp
(void) LuaUnlock(boolean, "addonName");
```
><b>G:</b> Вызов <strong><em>lua</em></strong> кода без блокировок:
```cpp
(bool) ... = Execute(...);
/* example:
    /run a,b,c = Execute("print(123)", "CastSpellByID(123, \"target\")","message('Hello World')");
    a = boolean;
    b = boolean;
    c = boolean; 
    в качестве возврата получаем информацию об успешном или нет применение.

    так-же можно использовать макрос
    /execute CastSpellByID(123, "target");
*/
```
><b>G:</b> Загрузка <strong><em>.lua</em></strong> файла в игру:
```cpp
(void) ExecuteFile("file");
/* example
    /run ExecuteFile("D:\\MyRotation\\core.lua");
*/
```
>L: Загрузить все <strong><em>.lua</em></strong> файлы из корневой папки программы:
```cpp
(void) LoadFromApp();
```
>L: Загрузить все <strong><em>.lua</em></strong> файлы из папки с вашим классом:
```cpp
(void) LoadFromClass();
```
>L: Открыть страницу в браузере по умолчанию
```cpp
(void) LaunchURL("url");
```
>L: Имя аддона из которого происходит вызов
```cpp
(string) addonName = GetCurrentAddOnName();
/* example
    /run api.LuaUnlock(true, GetCurrentAddonName());
*/
```
>L: Проверка нажатия клавиш
```cpp
(bool) ... = GetAsyncKeyState(... (KeyId));
/*
    /run a,s = api.GetAsyncKeyState(0x41, 0x53) if(a and s) then print("A and S is pressed!") end;
*/
```
***
## Работа с файлами/папками
+ (модули - это аналог функции require)
<br>


>L: Путь к папке с программой

```cpp
(string) value = GetAppDirectory();
/* example
    print(api.GetAppDirectory()) -- C:\\EasyWoW\\
*/
```

>L: Путь к папке с запущенным клиентов WoW

```cpp
(string) value = GetWoWDirectory();
/* example
    print(api.GetWoWDirectory()) -- C:\\Game\\World of Warcraft\\
*/
```
>L: Записать текст в файл

```cpp
(bool) result = FileWrite("file", "value");
/* example
    /run isGood = api.FileWrite("C:\\MyFile.txt", "Hello World");
    isGood = true или false в зависимости о том, удалось перезаписать файл или нет.
    Если файла не существует, он создастся по указаному пути.
*/
```
>L: Записать текст в конец файла.

```cpp
(bool) result = FileWriteLine("file", "value");
/* example
    /run isGood = api.FileWriteLine("C:\\MyFile.txt", "Hello World");
    isGood = true или false в зависимости о том, удалось перезаписать файл или нет.
    Если файла не существует, он создастся по указаному пути.
*/
```
>L: Загрузить в переменную содержимое файла в виде текста.
```cpp
(string) value = FileRead("file");
/* example
    /run text = api.FileRead("C:\\MyFile.txt"); print(text);
*/
```
>L: Проверка существование файла
```cpp
(bool) result = FileExist("file");
/* example
    /run isExist = api.FileExist("C:\\MyFile.txt");
    isExist = true or false;
*/
```
>L: Получение всех файлов в папке
```cpp
(table) value = GetFiles("directory"[,filter]);
/* example 
    /run files = api.GetFiles(api.GetAppDirectory(), "exe");
    files[1] = ERotation.exe;
*/
```
***
## Модули
>L: Загрузить модуль в клиент игры (используя исходный код)
```cpp
(bool) result = LoadModuleSource("moduleName", "source");
/* example
    /run result = api.LoadModuleSource("MyModule","return 1;");
    result = true or false;
*/
```
>L: Загрузить модуль в клиент игры (используя чтение файла)
```cpp
(bool) result = LoadModuleFile("moduleName", "file");
/* example
    /run result = api.LoadModuleSource("MyModule","C:\\MyModule.lua");
    result = true or false;
*/
```
>L: Проверка наличие модуля в клиенте игры
```cpp
(bool) result = ModuleIsLoaded("moduleName");
/* example
    /run isLoad = api.ModuleIsLoaded("MyModule");
    isLoad = true or false;
*/
```
>L: Список всех модулей
```cpp
(table) value = GetModules();
/* example
    /run moduleList = api.GetModules();
    moduleList[1] = MyModule;
*/
```
>L: Загрузка модуля в код
```cpp
(module) value = Module("name");
/* example
    /run spells = api.Module("Spells"); spells.Starfall:Cast("target");
*/
```
>L: Выгрузка модуля из клиента игры
```cpp
(void) RemoveModule("moduleName");
```
***

## Работа с памятью 

>L: Значение из памяти
```cpp
(int or string) value = MemoryRead("type", pointer[, offset]);
/* example
    /run value = api.MemoryRead("int", 0x12345678);
    value = 1;
*/
```
>L: Записать значение в указанный адрес памяти
```cpp
(void) MemoryWrite("type", pointer, value);
/* example
    /run api.MemoryWrite("string", 0x12345678, "ABC"); a = api.MemoryRead("string", 0x12345678);
*/
```
>L: Зарезервировать участок памяти
```cpp
(int) address = MemoryAllocate(size);
/* example 
    /run adr = api.MemoryAllocate(4); api.MemoryWrite("float", adr, 0.123);
*/
```
>L: Выгрузить участок памяти
```cpp
(bool) result = MemoryFree(address);
/* example 
    /run adr = api.MemoryAllocate(4); result = api.MemoryFree(adr);
*/
```
***

## Работа с игровыми объектами

>L: Количество объектов
```cpp
(int) object_count = GetObjectsCount();
```
>L: Список объектов
```cpp
(table) objects = GetObjects();
/* example
    for k,v in pairs(api.GetObjects()) do
        print(UnitName(v));
    end
*/
```
>L: Список объектов отсортированных по типу
```cpp
(table) objects = GetObjectsByType(... [typeId]);
/* example 
    сортировка юнитов и игроков
    for k,v in pairs(api.GetObjectsByType(3,4)) do
        print(UnitName(v));
    end
*/
```
>L: Позиция объекта
```cpp
(float) x,y,z = GetObjectPosition(unitId);
```
>L: Тип объекта
```cpp
(int) type = GetObjectType(unitId);
```
>L: Дистанция между точками/объектами (по трём осям)
```cpp
(float) distance = GetDistance(unitId_A or [x,y,z], [unitId_B or [x,y,z]);
```
>L: Дистанция между точками/объектами (по двум осям X и Y)
```cpp
(float) distance = GetDistance2D(unitId_A or [x,y], [unitId_B or [x,y]);
```
>L: Размер объекта
```cpp
(float) size = GetObjectSize(unitId);
```
>L: Множитель размера
```cpp
(float) scale = GetObjectScale(unitId);
(float) scale = GetObjectTrueScale(unitId);
```
>L: Номер объекта
```cpp
(int) id = GetObjectId(unitId);
```
>L: Указатель на объект
```cpp
(int) pointer = GetObjectPointer(unitId);
/* example
    /run ptr = api.GetObjectPointer("player"); guid = api.MemoryRead("int64", ptr, 0x8);
*/
```
>L: Взаимодействие с объектом
```cpp
(void) ObjectInteract(unitId);
```
>L: Объект стоит спиной
```cpp
(bool) result = ObjectIsBehind(unitId_a[,unitId_b]);
/* example
    /run if(api.ObjectIsBehind("target")) then print("Target is behind"); end;
*/
```
>L: Объект стоит лицом
```cpp
(bool) result = ObjectIsFacing(unitId_a[,unitId_b]);
/* example
    /run if(api.ObjectIsFacing("target", "focus")) then print("Фокус стоит лицом к таргету"); end;
*/
```
>L: Угол в который направлен объект
```cpp
(float) facing = GetFacing(unitId);
```
>L: Объект перед лицом
```cpp
(bool) result = IsInFront(unitId_a[,unitId_b]);
```
>L: Сторона направления объекта
```cpp
(float) sfacing = GetSideFacing(unitId);
```

***
## Игровой мир

>L: Информация о локации
```cpp
(int) mapId, (int) zoneId, (string) zoneName, (string) zoneSubName = GetCurrentMapInfo();
```
>L: Позиция камеры
```cpp
(float) x, y, z = GetCamPosition();
```
>L: Применить способность по местности
```cpp
(bool) result = GroundClick(x,y,z or (unitId[, CanHack]));
/* example 
    /run CastSpellByID(47820); api.GroundClick("target") -- применение по позиции таргета
    /run CastSpellByID(32375); api.GroundClick("target", true) -- применение в таргет.
*/
```
>L: Координаты коллизии между точками (преграды)
```cpp
(float) x, y, z = TraceLine(unitA [or x,y,z], unitB [or x,y,z], flag);
```
>L: Проверка препядствия на пути (не на всех сервера работотает корректно)
```cpp
(bool) result = LineOfSight(unitId_A or [x,y,z], [unitId_B or [x,y,z]);
/* example
    /run if(api.LineOfSight("player", "target")) then CastSpellByID(48441) end;
*/
```
>L: Перевод игровых координат в координаты для монитора
```cpp
(bool) isInScreen, (float)x,y = WorldToScreen([x,y,z] or UnitId);
```
***

## Рисование
>L: Нарисовать линию в игровом мире
```cpp
(void) DrawLine(unitA, unitB, r,g,b, size) or DrawLine(s_x,s_y,s_z, e_x,e_y,e_z, r,g,b, size);
/* example
    f = CreateFrame("Frame")
    f:SetScript("OnUpdate", function()
        if(UnitExists("target")) then
            api.DrawLine("player", "target", 255, 255, 255, 1);
        end;
    end);
    
*/
```
>L: Нарисовать текст в игровом мире
```cpp
(void) DrawText("Text", x,y,z, r,g,b, size);
/* example
    f = CreateFrame("Frame")
    f:SetScript("OnUpdate", function()
        if(UnitExists("target")) then
            local x,y,z = api.GetObjectPosition("player");
            api.DrawText("HelloWorld", x,y,z, 255, 255, 255, 14);
        end;
    end);
    
*/
```
>L: Нарисовать круг в игровом мире
```cpp
(void) DrawCircle([UnitId or x,y,z], range, r,g,b);
/* example
    f = CreateFrame("Frame")
    f:SetScript("OnUpdate", function()
        if(UnitExists("target")) then
            local x,y,z = api.GetObjectPosition("player");
            api.DrawCircle(x,y,z, 10, 255, 255, 255);
        end;
    end);
    
*/
```
***
## Разблокированные Lua функции из клиента
+ Сделано для обхода защит различных серверов

>L: Совмещённая функция CastSpellByID и CastSpellByName
```cpp
(void) SpellCast("spellName" or spellId[, target]);
```
>L: Использование предметов по имени или номеру
```cpp
(void) UseItemByNameOrID("itemName" or itemId);
```
>L: Номер способности по индексу стойки
```cpp
(int) spellId = GetSpellIdByShapeshiftIndex(index);
```
>L: Оригинальные функции
```cpp
(void) CastShapeshiftFormByIndex(index);
(void) SendAddonMessage("prefix", "text", "type" [, "player"]);
(void) AssistUnit(unitId);
(void) AttackTarget();
(void) ClearTarget();
(void) TargetLastEnemy();
(void) TargetLastTarget();
(void) TargetLastFriend();
(void) SpellTargetUnit(unitId);
(void) FocusUnit(unitId);
(void) ClearFocus();
(void) SpellStopTargeting();
(void) SpellStopCasting();
(void) ToggleSpellAutocast("spellName" | spellId, bookType);
(void) SetMultiCastSpell(actionID,spellID);
(void) CastPetAction(index);
(void) CastSpell(spellID, "bookType");
(void) PetAttack();
(void) JumpOrAscendStart();
(void) RunMacro(id or "name");
(void) RunMacroText("macrotext");
(void) StopMacro();
(void) UseInventoryItem(invSlot);
(void) UseContainerItem(bagID, slot[, onSelf]);
(void) CancelUnitBuff("unit", index or "spell" [,"filter" or "rank"]);
(void) CancelItemTempEnchantment(weaponHand);
(void) UseAction(slot[, checkCursor[, onSelf]]);
(void) PlaceAuctionBid("type", index, bid);
(void) CancelAuction(index);
(void) AcceptTrade();
(void) GuildInvite("playerName");
```
***
## Dynamic Objects
>L: Гуид создателя
```cpp
(string) guid = DynamicObjectsCasterGuid(unitId);
```
>L: Радиус
```cpp
(float) radius = DynamicObjectsRadius(unitId);
```
>L: Номер способности
```cpp
(int) spellId = DynamicObjectsSpellId(unitId);
```
>L: Время создания
```cpp
(int) castTime = DynamicObjectsCastTime(unitId);
```
***
## Units
>L: Список всех участников рейда
```cpp
(table) raid = GetRaidMembers();
```
>L: Список всех участников группы
```cpp
(table) party = GetPartyMembers();
```
>L: Список всех участников группы или рейда
```cpp
(table) group = GetGroupMembers();
```
>L: Юнит существует и находится в зоне видимости
```cpp
(bool) result = UnitIsValid(unitId);
```
>L: Можно собрать добычу
```cpp
(bool) result = UnitIsLootable(unitId);
```
>L: Открыто окно сбора добычи у этого юнита
```cpp
(bool) result = UnitIsLooting(unitId);
```
>L: У юнита осмотрели добычу
```cpp
(bool) result = UnitIsLooted(unitId);
```
>L: Юнит применяет заклинание
```cpp
(bool) result = UnitIsCasting(unitId);
```
>L: Юнит является продавцом еды
```cpp
(bool) result = UnitIsVendorFood(unitId);
```
>L: Юнит является продавцом
```cpp
(bool) result = UnitIsVendor(unitId);
```
>L: Юнит является продавцом реагентов
```cpp
(bool) result = UnitIsVendorReagent(unitId);
```
>L: Юнит может починить предметы
```cpp
(bool) result = UnitIsRepairer(unitId);
```
>L: Юнит - классовый тренер
```cpp
(bool) result = UnitIsClassTrainer(unitId);
```
>L: Юнит - тренер профессий
```cpp
(bool) result = UnitIsProfessionTrainer(unitId);
```
>L: Юнит - мастер полётов
```cpp
(bool) result = UnitIsFlightMaster(unitId);
```
>L: Юнит - хозяин таверны
```cpp
(bool) result = UnitIsInnkeeper(unitId);
```
>L: Юнит - Аукнционер
```cpp
(bool) result = UnitIsAuctioneer(unitId);
```
>L: Юнит - банкир
```cpp
(bool) result = UnitIsBanker(unitId);
```
>L: Юнит - даёт квесты
```cpp
(bool) result = UnitIsQuestGiver(unitId);
```
>L: Юнит - является тотемом
```cpp
(bool) result = UnitIsTotem(unitId);
```
>L: Юнит - является гильдейским банком
```cpp
(bool) result = UnitIsGuildBanker(unitId);
```
>L: С юнитом можно открыть диалог
```cpp
(bool) result = UnitIsGossip(unitId);
```
>L: Юнит - является почтой
```cpp
(bool) result = UnitIsMailBox(unitId);
```
>L: Юнит находится в бою
```cpp
(bool) result = UnitIsInCombat(unitId);
```
>L: Флаг передвижения юнита
```cpp
(bool) result = UnitGetMovementFlag(unitId);
```
>L: Проверка на наличие флага передвижения
```cpp
(bool) result = UnitMovementHasFlag(unitId, flag);
```
>L: Юнит передвигается
```cpp
(bool) result = UnitIsMoving(unitId);
```
>L: Юнит падает 
```cpp
(bool) result = UnitIsFalling(unitId);
```
>L: Список агрессивных юнитов в радиусе
```cpp
(table) enemy = GetEnemyInRange(range);
```
>L: Список дружелюбных юнитов в радиусе
```cpp
(table) friendly = GetFriendlyInRange(range);
```
>L: Список агрессивных юнитов в радиусе находящихся в бою
```cpp
(table) enemyInCombat = GetEnemyInCombatByRange(range);
```
>L: Гуид юнита на котором есть комбо-поинты
```cpp
(string) guid = GetComboPointsTarget();
```
***
## Игрок
>L: Передвижение в коодинаты
```cpp
(void) MoveTo(([x,y,z] or [unitId]) [,type_click]);
```
>L: Проверка на наличие активного передвижения к координате
```cpp
(bool) result = IsClickMoving();
```
>L: Остановить передвижение
```cpp
(void) StopMoving();
/* example
    /run if(api.IsClickMoving()) then api.StopMoving(); end;
*/
```
>L: Повернуть персонажа
```cpp
(void) SetFacing(float_value);
```
>L: Повернуться лицом к юниту/объекту
```cpp
(void) LookAt(unitId);
```
>L: Выбрать таргет
```cpp
(void) SetTarget(unitId);
```
>L: Телепортироваться <b>(HACK)</b>
```cpp
(void) Teleport(unitId or x,y,z [,boolean]);
```

***
## Game Object
>L: Тип игрового объекта
```cpp
(string) typeName, (int) typeId = GameObjectType(unitId);
```


