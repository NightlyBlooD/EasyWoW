# EasyWoW
<code>
(void) <b>ResetAFKTimer()</b></b>;<br>
(void) <b>ShowFPS(boolean or integer)</b>;<br>
(void) <b>EasyWoW(boolean or integer)</b>;<br>
(table)API, (table)ENUM = <b>EWAPI()</b>;<br>
(void) <b>LuaUnlock(boolean, "addonName")</b>;<br>
(boolean)... = <b>Execute(...)</b>;<br>
(void) <b>ExecuteFile("file")</b>;<br>
(void) <b>LoadFromApp()</b>;<br>
(void) <b>LoadFromClass()</b>;<br>
(boolean) result = <b>FileWrite("file", "value")</b>;<br>
(boolean) result = <b>FileWriteLine("file", "value")</b>;<br>
(string) value = <b>FileRead("file")</b>;<br>
(boolean) result = <b>FileExist("file")</b>;<br>
(string) value = <b>GetAppDirectory()</b>;<br>
(string) value = <b>GetWoWDirectory()</b>;<br>
(table) value = <b>GetFiles("directory")</b>;<br>
(module) value = <b>Module("name")</b>;<br>
(boolean) result = <b>LoadModuleSource("moduleName", "source")</b>;<br>
(boolean) result = <b>LoadModuleFile("moduleName", "file")</b>;<br>
(void) <b>RemoveModule("moduleName")</b>;<br>
(table) value = <b>GetModules()</b>;<br>
(boolean) result = <b>ModuleIsLoaded("moduleName")</b>;<br>
(int) object_count = <b>GetObjectsCount()</b>;<br>
(table) objects = <b>GetObjects()</b>;<br>
(table) objects = <b>GetObjectsByType(... [typeId])</b>;<br>
(float) x,y,z = <b>GetObjectPosition(unitId)</b>;<br>
(int) type = <b>GetObjectType(unitId)</b>;<br>
(float) distance = <b>GetDistance(unitId_A or [x,y,z], [unitId_B or [x,y,z])</b>;<br>
(float) distance = <b>GetDistance2D(unitId_A or [x,y], [unitId_B or [x,y])</b>;<br>
(float) size = <b>GetObjectSize(unitId)</b>;<br>
(float) scale = <b>GetObjectScale(unitId)</b>;<br>
(float) scale = <b>GetObjectTrueScale(unitId)</b>;<br>
(int) id = <b>GetObjectId(unitId)</b>;<br>
(int) pointer = <b>GetObjectPointer(unitId)</b>;<br>
(boolean) result = <b>LineOfSight(unitId_A or [x,y,z], [unitId_B or [x,y,z])</b>;<br>
(int) mapId, (int) zoneId, (string) zoneName, (string) zoneSubName = <b>GetCurrentMapInfo()</b>;<br>
(void) <b>ObjectInteract(unitId)</b>;<br>
(float) x, y, z = <b>TraceLine(unitA [or x,y,z], unitB [or x,y,z], flag)</b>;<br>
(void) <b>MoveTo(([x,y,z] or [unitId]) [,type_click])</b>;<br>
(boolean) result = <b>IsClickMoving()</b>;<br>
(void) <b>StopMoving()</b>;<br>
(void) <b>SetFacing(float_value)</b>;<br>
(void) <b>LookAt(unitId)</b>;<br>
(float) facing = <b>GetFacing(unitId)</b>;<br>
(boolean) result = <b>IsInFront(unitId_a[,unitId_b])</b>;<br>
(float) sfacing = <b>GetSideFacing(unitId)</b>;<br>
(void) <b>SpellCast("spellName" or spellId[, target])</b>;<br>
(boolean) result = <b>GroundClick(x,y,z [or unitId])</b>;<br>
(float) x, y, z = <b>GetCamPosition()</b>;<br>
(boolean) result = <b>ObjectIsBehind(unitId_a[,unitId_b])</b>;<br>
(boolean) result = <b>ObjectIsFacing(unitId_a[,unitId_b])</b>;<br>
(boolean) ... = <b>GetAsyncKeyState(... (KeyId))</b>;<br>
(void) <b>UseItemByNameOrID("itemName" or itemId)</b>;<br>
(int) spellId = <b>GetSpellIdByShapeshiftIndex(index)</b>;<br>
(void) <b>CastShapeshiftFormByIndex(index)</b>;<br>
(void) <b>SendAddonMessage("prefix", "text", "type" [, "player"])</b>;<br>
(void) <b>AssistUnit(unitId)</b>;<br>
(void) <b>AttackTarget()</b>;<br>
(void) <b>ClearTarget()</b>;<br>
(void) <b>TargetLastEnemy()</b>;<br>
(void) <b>TargetLastTarget()</b>;<br>
(void) <b>TargetLastFriend()</b>;<br>
(void) <b>SpellTargetUnit(unitId)</b>;<br>
(void) <b>FocusUnit(unitId)</b>;<br>
(void) <b>ClearFocus()</b>;<br>
(void) <b>SpellStopTargeting()</b>;<br>
(void) <b>SpellStopCasting()</b>;<br>
(void) <b>ToggleSpellAutocast("spellName" | spellId, bookType)</b>;<br>
(void) <b>SetMultiCastSpell(actionID,spellID)</b>;<br>
(void) <b>CastPetAction(index)</b>;<br>
(void) <b>CastSpell(spellID, "bookType")</b>;<br>
(void) <b>PetAttack()</b>;<br>
(void) <b>JumpOrAscendStart()</b>;<br>
(void) <b>RunMacro(id or "name")</b>;<br>
(void) <b>RunMacroText("macrotext")</b>;<br>
(void) <b>StopMacro()</b>;<br>
(void) <b>UseInventoryItem(invSlot)</b>;<br>
(void) <b>UseContainerItem(bagID, slot[, onSelf])</b>;<br>
(void) <b>CancelUnitBuff("unit", index or "spell" [,"filter" or "rank"])</b>;<br>
(void) <b>CancelItemTempEnchantment(weaponHand)</b>;<br>
(void) <b>UseAction(slot[, checkCursor[, onSelf]])</b>;<br>
(void) <b>PlaceAuctionBid("type", index, bid)</b>;<br>
(void) <b>CancelAuction(index)</b>;<br>
(void) <b>AcceptTrade()</b>;<br>
(void) <b>GuildInvite("playerName")</b>;<br>
(void) <b>LaunchURL("url")</b>;<br>
(void) <b>Teleport(unitId or x,y,z [,boolean])</b>;<br>
(string) guid = <b>DynamicObjectsCasterGuid(unitId)</b>;<br>
(float) radius = <b>DynamicObjectsRadius(unitId)</b>;<br>
(int) spellId = <b>DynamicObjectsSpellId(unitId)</b>;<br>
(int) castTime = <b>DynamicObjectsCastTime(unitId)</b>;<br>
(table) raid = <b>GetRaidMembers()</b>;<br>
(table) party = <b>GetPartyMembers()</b>;<br>
(table) group = <b>GetGroupMembers()</b>;<br>
(boolean) result = <b>UnitIsValid(unitId)</b>;<br>
(boolean) result = <b>UnitIsLootable(unitId)</b>;<br>
(boolean) result = <b>UnitIsLooting(unitId)</b>;<br>
(boolean) result = <b>UnitIsLooted(unitId)</b>;<br>
(boolean) result = <b>UnitIsCasting(unitId)</b>;<br>
(boolean) result = <b>UnitIsVendorFood(unitId)</b>;<br>
(boolean) result = <b>UnitIsVendor(unitId)</b>;<br>
(boolean) result = <b>UnitIsVendorReagent(unitId)</b>;<br>
(boolean) result = <b>UnitIsRepairer(unitId)</b>;<br>
(boolean) result = <b>UnitIsClassTrainer(unitId)</b>;<br>
(boolean) result = <b>UnitIsProfessionTrainer(unitId)</b>;<br>
(boolean) result = <b>UnitIsFlightMaster(unitId)</b>;<br>
(boolean) result = <b>UnitIsInnkeeper(unitId)</b>;<br>
(boolean) result = <b>UnitIsAuctioneer(unitId)</b>;<br>
(boolean) result = <b>UnitIsBanker(unitId)</b>;<br>
(boolean) result = <b>UnitIsQuestGiver(unitId)</b>;<br>
(boolean) result = <b>UnitIsTotem(unitId)</b>;<br>
(boolean) result = <b>UnitIsGuildBanker(unitId)</b>;<br>
(boolean) result = <b>UnitIsGossip(unitId)</b>;<br>
(boolean) result = <b>UnitIsMailBox(unitId)</b>;<br>
(boolean) result = <b>UnitIsInCombat(unitId)</b>;<br>
(boolean) result = <b>UnitGetMovementFlag(unitId)</b>;<br>
(boolean) result = <b>UnitMovementHasFlag(unitId, flag)</b>;<br>
(boolean) result = <b>UnitIsMoving(unitId)</b>;<br>
(boolean) result = <b>UnitIsFalling(unitId)</b>;<br>
(string) typeName, (int) typeId = <b>GameObjectType(unitId)</b>;<br>
(table) enemy = <b>GetEnemyInRange(range)</b>;<br>
(table) friendly = <b>GetFriendlyInRange(range)</b>;<br>
(table) enemyInCombat = <b>GetEnemyInCombatByRange(range)</b>;<br>
(string) guid = <b>GetComboPointsTarget()</b>;<br>
(void) <b>SetTarget(unitId)</b>;<br>
(boolean) isInScreen, (float)x,y = <b>WorldToScreen([x,y,z] or UnitId)</b>;<br>
(void) <b>DrawLine(unitA, unitB, r,g,b, size) or DrawLine(s_x,s_y,s_z, e_x,e_y,e_z, r,g,b, size)</b>;<br>
(void) <b>DrawText("Text", x,y,z, r,g,b, size)</b>;<br>
(void) <b>DrawCircle([UnitId or x,y,z], range, r,g,b)</b>;<br>
(string) addonName = <b>GetCurrentAddOnName()</b>;<br>
(int or string) value = <b>MemoryRead("type", pointer[, offset])</b>;<br>
(void) <b>MemoryWrite("type", pointer, value)</b>;<br>
(int) address = <b>MemoryAllocate(size)</b>;<br>
(boolean) result = <b>MemoryFree(address)</b>;<br>
</code>
