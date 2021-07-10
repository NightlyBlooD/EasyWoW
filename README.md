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
#

## Системные функции

>L: Сброс афк таймера:
```C#
(void) ResetAFKTimer();
```
>L: Показать счётчик FPS:
```C#
(void) ShowFPS(boolean or integer)
```
>L: Показать/Скрыть окно программы:
```C#
(void) EasyWoW(boolean or integer);
```
><b>G:</b> Инициализации локальных API и таблиц:
```C#
(table) API, ENUMs = EWAPI(); 
/* example:
    /run api = EWAPI() api.ResetAFKTimer();
*/
```

>L: Разблокировка луа для определённого аддона:
```C#
(void) LuaUnlock(boolean, "addonName");
```
><b>G:</b> Вызов <strong><em>lua</em></strong> кода без блокировок:
```C#
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
```C#
(void) ExecuteFile("file");
/* example
    /run ExecuteFile("D:\\MyRotation\\core.lua");
*/
```
>L: Загрузить все <strong><em>.lua</em></strong> файлы из корневой папки программы:
```C#
(void) LoadFromApp();
```
>L: Загрузить все <strong><em>.lua</em></strong> файлы из папки с вашим классом:
```C#
(void) LoadFromClass();
```
>L: Загрузка и выполение кода в буфере Lua
```C#
(object) LoadBuffer("source");
```

>L: Открыть страницу в браузере по умолчанию
```C#
(void) LaunchURL("url");
```
>L: Имя аддона из которого происходит вызов
```C#
(string) addonName = GetCurrentAddOnName();
/* example
    /run api.LuaUnlock(true, GetCurrentAddonName());
*/
```
>L: Проверка нажатия клавиш
```C#
(bool) ... = GetAsyncKeyState(... (KeyId));
/*
    /run a,s = api.GetAsyncKeyState(0x41, 0x53) if(a and s) then print("A and S is pressed!") end;
*/
```
***

## Работа с файлами/папками



>L: Путь к папке с программой

```C#
(string) value = GetAppDirectory();
/* example
    print(api.GetAppDirectory()) -- C:\\EasyWoW\\
*/
```

>L: Путь к папке с запущенным клиентов WoW

```C#
(string) value = GetWoWDirectory();
/* example
    print(api.GetWoWDirectory()) -- C:\\Game\\World of Warcraft\\
*/
```
>L: Записать текст в файл

```C#
(bool) result = FileWrite("file", "value");
/* example
    /run isGood = api.FileWrite("C:\\MyFile.txt", "Hello World");
    isGood = true или false в зависимости о том, удалось перезаписать файл или нет.
    Если файла не существует, он создастся по указаному пути.
*/
```
>L: Записать текст в конец файла.

```C#
(bool) result = FileWriteLine("file", "value");
/* example
    /run isGood = api.FileWriteLine("C:\\MyFile.txt", "Hello World");
    isGood = true или false в зависимости о том, удалось перезаписать файл или нет.
    Если файла не существует, он создастся по указаному пути.
*/
```
>L: Загрузить в переменную содержимое файла в виде текста.
```C#
(string) value = FileRead("file");
/* example
    /run text = api.FileRead("C:\\MyFile.txt"); print(text);
*/
```
>L: Проверка существование файла
```C#
(bool) result = FileExist("file");
/* example
    /run isExist = api.FileExist("C:\\MyFile.txt");
    isExist = true or false;
*/
```
>L: Получение всех файлов в папке
```C#
(table) value = GetFiles("directory"[,filter]);
/* example 
    /run files = api.GetFiles(api.GetAppDirectory(), "exe");
    files[1] = ERotation.exe;
*/
```
***

## Модули
+ (модули - это аналог функции require)
<br>

>L: Загрузить модуль в клиент игры (используя исходный код)
```C#
(bool) result = LoadModuleSource("moduleName", "source");
/* example
    /run result = api.LoadModuleSource("MyModule","return 1;");
    result = true or false;
*/
```
>L: Загрузить модуль в клиент игры (используя чтение файла)
```C#
(bool) result = LoadModuleFile("moduleName", "file");
/* example
    /run result = api.LoadModuleSource("MyModule","C:\\MyModule.lua");
    result = true or false;
*/
```
>L: Проверка наличие модуля в клиенте игры
```C#
(bool) result = ModuleIsLoaded("moduleName");
/* example
    /run isLoad = api.ModuleIsLoaded("MyModule");
    isLoad = true or false;
*/
```
>L: Список всех модулей
```C#
(table) value = GetModules();
/* example
    /run moduleList = api.GetModules();
    moduleList[1] = MyModule;
*/
```
>L: Загрузка модуля в код
```C#
(module) value = Module("name");
/* example
    /run spells = api.Module("Spells"); spells.Starfall:Cast("target");
*/
```
>L: Выгрузка модуля из клиента игры
```C#
(void) RemoveModule("moduleName");
```
***

## Работа с памятью 

>L: Значение из памяти
```C#
(int or string) value = MemoryRead("type", pointer[, offset]);
/* example
    /run value = api.MemoryRead("int", 0x12345678);
    value = 1;
*/
```
>L: Записать значение в указанный адрес памяти
```C#
(void) MemoryWrite("type", pointer, value);
/* example
    /run api.MemoryWrite("string", 0x12345678, "ABC"); a = api.MemoryRead("string", 0x12345678);
*/
```
>L: Зарезервировать участок памяти
```C#
(int) address = MemoryAllocate(size);
/* example 
    /run adr = api.MemoryAllocate(4); api.MemoryWrite("float", adr, 0.123);
*/
```
>L: Выгрузить участок памяти
```C#
(bool) result = MemoryFree(address);
/* example 
    /run adr = api.MemoryAllocate(4); result = api.MemoryFree(adr);
*/
```
***



## Игровой мир

>L: Информация о локации
```C#
(int) mapId, (int) zoneId, (string) zoneName, (string) zoneSubName = GetCurrentMapInfo();
```
>L: Позиция камеры
```C#
(float) x, y, z = GetCamPosition();
```
>L: Применить способность по местности
```C#
(bool) result = GroundClick(x,y,z or (unitId[, CanHack]));
/* example 
    /run CastSpellByID(47820); api.GroundClick("target") -- применение по позиции таргета
    /run CastSpellByID(32375); api.GroundClick("target", true) -- применение в таргет.
*/
```
>L: Координаты коллизии между точками (преграды)
```C#
(float) x, y, z = TraceLine(unitA [or x,y,z], unitB [or x,y,z], flag);
```
>L: Проверка препядствия на пути (не на всех сервера работотает корректно)
```C#
(bool) result = LineOfSight(unitId_A or [x,y,z], [unitId_B or [x,y,z]);
/* example
    /run if(api.LineOfSight("player", "target")) then CastSpellByID(48441) end;
*/
```
>L: Перевод игровых координат в координаты для монитора
```C#
(bool) isInScreen, (float)x,y = WorldToScreen([x,y,z] or UnitId);
```
***

## Рисование
>L: Нарисовать линию в игровом мире
```C#
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
```C#
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
```C#
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

## Работа с объектами

>L: Количество объектов
```C#
(int) object_count = GetObjectsCount();
```
>L: Список объектов
```C#
(table) objects = GetObjects();
/* example
    for k,v in pairs(api.GetObjects()) do
        print(UnitName(v));
    end
*/
```
>L: Список объектов отсортированных по типу
```C#
(table) objects = GetObjectsByType(... [typeId]);
/* example 
    сортировка юнитов и игроков
    for k,v in pairs(api.GetObjectsByType(3,4)) do
        print(UnitName(v));
    end
*/
```
>L: Позиция объекта
```C#
(float) x,y,z = GetObjectPosition(unitId);
```
>L: Тип объекта
```C#
(int) type = GetObjectType(unitId);
```
>L: Дистанция между точками/объектами (по трём осям)
```C#
(float) distance = GetDistance(unitId_A or [x,y,z], [unitId_B or [x,y,z]);
```
>L: Дистанция между точками/объектами (по двум осям X и Y)
```C#
(float) distance = GetDistance2D(unitId_A or [x,y], [unitId_B or [x,y]);
```
>L: Размер объекта
```C#
(float) size = GetObjectSize(unitId);
```
>L: Множитель размера
```C#
(float) scale = GetObjectScale(unitId);
(float) scale = GetObjectTrueScale(unitId);
```
>L: Номер объекта
```C#
(int) id = GetObjectId(unitId);
```
>L: Указатель на объект
```C#
(int) pointer = GetObjectPointer(unitId);
/* example
    /run ptr = api.GetObjectPointer("player"); guid = api.MemoryRead("int64", ptr, 0x8);
*/
```
>L: Взаимодействие с объектом
```C#
(void) ObjectInteract(unitId);
```
>L: Объект стоит спиной
```C#
(bool) result = ObjectIsBehind(unitId_a[,unitId_b]);
/* example
    /run if(api.ObjectIsBehind("target")) then print("Target is behind"); end;
*/
```
>L: Объект стоит лицом
```C#
(bool) result = ObjectIsFacing(unitId_a[,unitId_b]);
/* example
    /run if(api.ObjectIsFacing("target", "focus")) then print("Фокус стоит лицом к таргету"); end;
*/
```
>L: Угол в который направлен объект
```C#
(float) facing = GetFacing(unitId);
```
>L: Объект перед лицом
```C#
(bool) result = IsInFront(unitId_a[,unitId_b]);
```
>L: Сторона направления объекта
```C#
(float) sfacing = GetSideFacing(unitId);
```

***

## Units
>L: Список всех участников рейда
```C#
(table) raid = GetRaidMembers();
```
>L: Список всех участников группы
```C#
(table) party = GetPartyMembers();
```
>L: Список всех участников группы или рейда
```C#
(table) group = GetGroupMembers();
```
>L: Юнит существует и находится в зоне видимости
```C#
(bool) result = UnitIsValid(unitId);
```
>L: Можно собрать добычу
```C#
(bool) result = UnitIsLootable(unitId);
```
>L: Открыто окно сбора добычи у этого юнита
```C#
(bool) result = UnitIsLooting(unitId);
```
>L: У юнита осмотрели добычу
```C#
(bool) result = UnitIsLooted(unitId);
```
>L: Юнит применяет заклинание
```C#
(bool) result = UnitIsCasting(unitId);
```
>L: Юнит является продавцом еды
```C#
(bool) result = UnitIsVendorFood(unitId);
```
>L: Юнит является продавцом
```C#
(bool) result = UnitIsVendor(unitId);
```
>L: Юнит является продавцом реагентов
```C#
(bool) result = UnitIsVendorReagent(unitId);
```
>L: Юнит может починить предметы
```C#
(bool) result = UnitIsRepairer(unitId);
```
>L: Юнит - классовый тренер
```C#
(bool) result = UnitIsClassTrainer(unitId);
```
>L: Юнит - тренер профессий
```C#
(bool) result = UnitIsProfessionTrainer(unitId);
```
>L: Юнит - мастер полётов
```C#
(bool) result = UnitIsFlightMaster(unitId);
```
>L: Юнит - хозяин таверны
```C#
(bool) result = UnitIsInnkeeper(unitId);
```
>L: Юнит - Аукнционер
```C#
(bool) result = UnitIsAuctioneer(unitId);
```
>L: Юнит - банкир
```C#
(bool) result = UnitIsBanker(unitId);
```
>L: Юнит - даёт квесты
```C#
(bool) result = UnitIsQuestGiver(unitId);
```
>L: Юнит - является тотемом
```C#
(bool) result = UnitIsTotem(unitId);
```
>L: Юнит - является гильдейским банком
```C#
(bool) result = UnitIsGuildBanker(unitId);
```
>L: С юнитом можно открыть диалог
```C#
(bool) result = UnitIsGossip(unitId);
```
>L: Юнит - является почтой
```C#
(bool) result = UnitIsMailBox(unitId);
```
>L: Юнит находится в бою
```C#
(bool) result = UnitIsInCombat(unitId);
```
>L: Флаг передвижения юнита
```C#
(bool) result = UnitGetMovementFlag(unitId);
```
>L: Проверка на наличие флага передвижения
```C#
(bool) result = UnitMovementHasFlag(unitId, flag);
```
>L: Юнит передвигается
```C#
(bool) result = UnitIsMoving(unitId);
```
>L: Юнит падает 
```C#
(bool) result = UnitIsFalling(unitId);
```
>L: Список агрессивных юнитов в радиусе
```C#
(table) enemy = GetEnemyInRange(range);
```
>L: Список дружелюбных юнитов в радиусе
```C#
(table) friendly = GetFriendlyInRange(range);
```
>L: Список агрессивных юнитов в радиусе находящихся в бою
```C#
(table) enemyInCombat = GetEnemyInCombatByRange(range);
```
>L: GUID юнита на котором есть комбо-поинты
```C#
(string) guid = GetComboPointsTarget();
```
***

## Игрок
>L: Передвижение в коодинаты
```C#
(void) MoveTo(([x,y,z] or [unitId]) [,type_click]);
```
>L: Проверка на наличие активного передвижения к координате
```C#
(bool) result = IsClickMoving();
```
>L: Остановить передвижение
```C#
(void) StopMoving();
/* example
    /run if(api.IsClickMoving()) then api.StopMoving(); end;
*/
```
>L: Повернуть персонажа
```C#
(void) SetFacing(float_value);
```
>L: Повернуться лицом к юниту/объекту
```C#
(void) LookAt(unitId);
```
>L: Выбрать таргет
```C#
(void) SetTarget(unitId);
```
>L: Телепортироваться <b>(HACK)</b>
```C#
(void) Teleport(unitId or x,y,z [,boolean]);
```

***

## Game Object
>L: Тип игрового объекта
```C#
(string) typeName, (int) typeId = GameObjectType(unitId);
```
>L: GUID создателя
```C#
(string) guid = GameObjectCreatedGuid(unitId);
```
>L: Вы создатель GameObject
```C#
(bool) isMine = GameObjectIsMine(unitId);
```


## Dynamic Objects
>L: GUID создателя
```C#
(string) guid = DynamicObjectCasterGuid(unitId);
```
>L: Вы создатель DynamicObject
```C#
(bool) isMine = DynamicObjectIsMine(unitId);
```
>L: Радиус
```C#
(float) radius = DynamicObjectRadius(unitId);
```
>L: Номер способности
```C#
(int) spellId = DynamicObjectSpellId(unitId);
```
>L: Время создания
```C#
(int) castTime = DynamicObjectCastTime(unitId);
```
***

## Spell
>L: Номер применияемого заклинания юнитом
```C#
(int) spellId = GetCastingSpellId(unitId);
```
>L: Номер потокового заклинания приминяемого юнитом
```C#
(int) spellId = GetChanneledSpellId(unitId);
```
>L: Информация о применяемой способности юнитом
```C#
(int) spellId, 
(string) spellName, 
(string) rank, 
(string) spellMechanicName, 
(int) spellMechanic, 
(table int) spellEffect[3], 
(table string) spellEffectName[3], 
(float) timeToEndCast, 
(float) minRange, 
(float) maxRange, 
(bool) isImmuneInterrupt 
= UnitCastingInfo(unitId);
```
>L: Информация о применяемой потоковой способности юнитом
```C#
(int) spellId, 
(string) spellName, 
(string) rank, 
(string) spellMechanicName, 
(int) spellMechanic, 
(table int) spellEffect[3],
(table string) spellEffectName[3],  
(float) timeToEndCast, 
(float) minRange, 
(float) maxRange, 
(bool) isImmuneInterrupt 
= UnitChanneledInfo(unitId);
```
>L: Механика споcобности
```C#
(int) mechanicId, (string) mechanicName = GetSpellMechanic(spellName or spellId);
```
>L: Эффект споcобности
```C#
(int) eff1, eff2, eff3 = GetSpellEffect(spellName or spellId);
```
>L: Эффект споcобности
```C#
(string) eff1, eff2, eff3 = GetSpellEffectName(spellName or spellId);
```
>L: Дальность применения споcобности
```C#
(float) minRange, maxRange = GetSpellRange(spellName or spellId [, unitId]);
```
>L: Количество изученных способностей
```C#
(int) spellCount = GetSpellCount();
```
>L: Информация о изученной способности по номеру в книге заклинаний
```C#
(int) spellId, 
(string) spellName, 
(string) rank,
(int) castTime, 
(int) powerCost,
(int) spellMechanic, 
(string) spellMechanicName 
= GetSpellBySpellBookIndex();
```

***

## Разблокированные Lua функции из клиента
+ Сделано для обхода защит различных серверов

>L: Совмещённая функция CastSpellByID и CastSpellByName
```C#
(void) SpellCast("spellName" or spellId[, target]);
```
>L: Использование предметов по имени или номеру
```C#
(void) UseItemByNameOrID("itemName" or itemId);
```
>L: Номер способности по индексу стойки
```C#
(int) spellId = GetSpellIdByShapeshiftIndex(index);
```
>L: Оригинальные WoW API функции
```C#
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
