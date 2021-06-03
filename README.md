# EasyWoW
(void) ResetAFKTimer()
(void) ShowFPS(boolean or integer)
(void) EasyWoW(boolean or integer)
(table)API, (table)ENUM = EWAPI()
(void) LuaUnlock(boolean, "addonName")
(boolean)... = Execute(...)
(void) ExecuteFile("file")
(void) LoadFromApp()
(void) LoadFromClass()
(boolean) result = FileWrite("file", "value")
(boolean) result = FileWriteLine("file", "value")
(string) value = FileRead("file")
(boolean) result = FileExist("file")
(string) value = GetAppDirectory()
(string) value = GetWoWDirectory();
(table) value = GetFiles("directory")
(module) value = Module("name")
(boolean) result = LoadModuleSource("moduleName", "source")
(boolean) result = LoadModuleFile("moduleName", "file")
(void) RemoveModule("moduleName")
(table) value = GetModules()
(boolean) result = ModuleIsLoaded("moduleName")
(int) object_count = GetObjectsCount()
(table) objects = GetObjects()
(table) objects = GetObjectsByType(... [typeId])
(float) x,y,z = GetObjectPosition(unitId)
(int) type = GetObjectType(unitId)
(float) distance = GetDistance(unitId_A or [x,y,z], [unitId_B or [x,y,z])
(float) distance = GetDistance2D(unitId_A or [x,y], [unitId_B or [x,y])
(float) size = GetObjectSize(unitId)
(float) scale = GetObjectScale(unitId)
(float) scale = GetObjectTrueScale(unitId)
(int) id = GetObjectId(unitId)
(int) pointer = GetObjectPointer(unitId)
(boolean) result = LineOfSight(unitId_A or [x,y,z], [unitId_B or [x,y,z])
(int) mapId, (int) zoneId, (string) zoneName, (string) zoneSubName = GetCurrentMapInfo()
(void) ObjectInteract(unitId)
(float) x, y, z = TraceLine(unitA [or x,y,z], unitB [or x,y,z], flag)
(void) MoveTo(([x,y,z] or [unitId]) [,type_click])
(boolean) result = IsClickMoving()
(void) StopMoving()
(void) SetFacing(float_value)
(void) LookAt(unitId)
(float) facing = GetFacing(unitId)
(boolean) result = IsInFront(unitId_a[,unitId_b])
(float) sfacing GetSideFacing(unitId)
(void) SpellCast("spellName" or spellId[, target])
(boolean) result = GroundClick(x,y,z [or unitId])
(float) x, y, z = GetCamPosition()
(boolean) result = ObjectIsBehind(unitId_a[,unitId_b])
(boolean) result = ObjectIsFacing(unitId_a[,unitId_b])
(boolean) ... = GetAsyncKeyState(... (KeyId))
(void) UseItemByNameOrID("itemName" or itemId)
(int) spellId = GetSpellIdByShapeshiftIndex(index)
(void) CastShapeshiftFormByIndex(index)
(void) SendAddonMessage("prefix", "text", "type" [, "player"])
(void) AssistUnit(unitId)
(void) AttackTarget()
(void) ClearTarget()
(void) TargetLastEnemy()
(void) TargetLastTarget()
(void) TargetLastFriend()
(void) SpellTargetUnit(unitId)
(void) FocusUnit(unitId)
(void) ClearFocus()
(void) SpellStopTargeting()
(void) SpellStopCasting()
(void) ToggleSpellAutocast("spellName" | spellId, bookType)
(void) SetMultiCastSpell(actionID,spellID)
(void) CastPetAction(index)
(void) CastSpell(spellID, "bookType")
(void) PetAttack()
(void) JumpOrAscendStart()
(void) RunMacro(id or "name")
(void) RunMacroText("macrotext")
(void) StopMacro()
(void) UseInventoryItem(invSlot)
(void) UseContainerItem(bagID, slot[, onSelf])
(void) CancelUnitBuff("unit", index or "spell" [,"filter" or "rank"])
(void) CancelItemTempEnchantment(weaponHand)
(void) UseAction(slot[, checkCursor[, onSelf]])
(void) PlaceAuctionBid("type", index, bid)
(void) CancelAuction(index)
(void) AcceptTrade()
(void) GuildInvite("playerName")
(void) LaunchURL("url")
(void) Teleport(unitId or x,y,z [,boolean])
(string) guid = DynamicObjectsCasterGuid(unitId)
(float) radius = DynamicObjectsRadius(unitId)
(int) spellId = DynamicObjectsSpellId(unitId)
(int) castTime = DynamicObjectsCastTime(unitId)
(table) raid = GetRaidMembers()
(table) party = GetPartyMembers()
(table) group = GetGroupMembers()
(boolean) result = UnitIsValid(unitId)
(boolean) result = UnitIsLootable(unitId)
(boolean) result = UnitIsLooting(unitId)
(boolean) result = UnitIsLooted(unitId)
(boolean) result = UnitIsCasting(unitId)
(boolean) result = UnitIsVendorFood(unitId)
(boolean) result = UnitIsVendor(unitId)
(boolean) result = UnitIsVendorReagent(unitId)
(boolean) result = UnitIsRepairer(unitId)
(boolean) result = UnitIsClassTrainer(unitId)
(boolean) result = UnitIsProfessionTrainer(unitId)
(boolean) result = UnitIsFlightMaster(unitId)
(boolean) result = UnitIsInnkeeper(unitId)
(boolean) result = UnitIsAuctioneer(unitId)
(boolean) result = UnitIsBanker(unitId)
(boolean) result = UnitIsQuestGiver(unitId)
(boolean) result = UnitIsTotem(unitId)
(boolean) result = UnitIsGuildBanker(unitId)
(boolean) result = UnitIsGossip(unitId)
(boolean) result = UnitIsMailBox(unitId)
(boolean) result = UnitIsInCombat(unitId)
(boolean) result = UnitGetMovementFlag(unitId)
(boolean) result = UnitMovementHasFlag(unitId, flag)
(boolean) result = UnitIsMoving(unitId)
(boolean) result = UnitIsFalling(unitId)
(string) typeName, (int) typeId = GameObjectType(unitId);
(table) enemy = GetEnemyInRange(range)
(table) friendly = GetFriendlyInRange(range)
(table) enemyInCombat = GetEnemyInCombatByRange(range)
(string) guid = GetComboPointsTarget()
(void) SetTarget(unitId)
(boolean) isInScreen, (float)x,y = WorldToScreen([x,y,z] or UnitId)
(void) DrawLine(unitA, unitB, r,g,b, size) or DrawLine(s_x,s_y,s_z, e_x,e_y,e_z, r,g,b, size)
(void) DrawText("Text", x,y,z, r,g,b, size)
(void) DrawCircle([UnitId or x,y,z], range, r,g,b)
(string) addonName = GetCurrentAddOnName()
(int or string) value = MemoryRead("type", pointer[, offset])
(void) MemoryWrite("type", pointer, value)
(int) address = MemoryAllocate(size)
(boolean) result = MemoryFree(address)
