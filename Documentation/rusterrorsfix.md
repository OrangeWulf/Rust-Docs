# AnalyzeConfigurationServiceLastDevBlog

## Analyze Base Models
This section contains rules for analyzing and fixing code errors. Each rule describes the error type, provides a regex pattern to search for the issue, and the solution.

### Error: .е удается преобразовать (тип|из) "(NetworkableId|ItemId|ItemContainerId)" в "(ulong|uint)"
Description of the problem: Исправляет ошибку, связанную с попыткой преобразовать (NetworkableId|ItemId|ItemContainerId) в (ulong|uint), добавляя вызов свойства .Value для получения значения типа ulong.

- Where to look for the error: This rule analyzes directly at the point of the error.
- Regex pattern to search: $this
- How it will be fixed: $this.Value
- Elements impacted by the fix: The fix applies to all elements in the code.

### Error: Непредвиденная директива препроцессору
Description of the problem: Удаляет неожиданную директиву препроцессора, которая вызывает ошибку.

- Where to look for the error: This rule analyzes the entire code.
- Regex pattern to search: \s*#(region|endregion).*
- How it will be fixed: 
- Elements impacted by the fix: The fix applies to all elements in the code.

### Error: Требуется директива #endregion
Description of the problem: Удаляет все директивы #region и #endregion.

- Where to look for the error: This rule analyzes the entire code.
- Regex pattern to search: \s*#(region|endregion).*
- How it will be fixed: 
- Elements impacted by the fix: The fix applies to all elements in the code.

### Error: Недопустимый термин "ulong" в выражении
Description of the problem: Заменяет недопустимый тип ulong на UInt32.

- Where to look for the error: This rule analyzes directly at the point of the error.
- Regex pattern to search: $this
- How it will be fixed: UInt32
- Elements impacted by the fix: The fix applies to all elements in the code.

### Error: Аргумент 1: не удается преобразовать из "NetworkableId" в "ulong"
Description of the problem: Добавляет .Value для преобразования NetworkableId в ulong.

- Where to look for the error: This rule analyzes directly at the point of the error.
- Regex pattern to search: (\w+)\.net\.ID
- How it will be fixed: $1.net.ID.Value
- Elements impacted by the fix: The fix applies to all elements in the code.

### Error: Не удается неявно преобразовать тип "NetworkableId" в "ulong"
Description of the problem: Добавляет .Value для преобразования NetworkableId в ulong.

- Where to look for the error: This rule analyzes directly at the point of the error.
- Regex pattern to search: \.net\.ID
- How it will be fixed: .net.ID.Value
- Elements impacted by the fix: The fix applies to all elements in the code.

### Error: Оператор "\?\?" невозможно применить к операнду типа "(NetworkableId|ItemId|ItemContainerId)\??" и "int"
Description of the problem: Заменяет .net.ID ?? 0 на .net.ID.Value ?? 0, чтобы исправить ошибку с оператором ??

- Where to look for the error: This rule analyzes directly at the point of the error.
- Regex pattern to search: \.net\.ID\s*\?\?\s*0
- How it will be fixed: .net.ID.Value ?? 0
- Elements impacted by the fix: The fix applies to all elements in the code.

### Error: Аргумент 1: не удается преобразовать из "ulong" в "(NetworkableId|ItemId|ItemContainerId)"
Description of the problem: Заменяет передачу ulong в метод, ожидающий NetworkableId, на использование конструктора NetworkableId.

- Where to look for the error: This rule analyzes directly at the point of the error.
- Regex pattern to search: $this
- How it will be fixed: new $errorGroup1($this)
- Elements impacted by the fix: The fix applies to all elements in the code.

### Error: Аргумент 1: не удается преобразовать из "uint" в "(NetworkableId|ItemId|ItemContainerId)"
Description of the problem: Создает объект NetworkableId, ItemId или ItemContainerId из uint значения.

- Where to look for the error: This rule analyzes directly at the point of the error.
- Regex pattern to search: $this
- How it will be fixed: new $errorGroup1($this)
- Elements impacted by the fix: The fix applies to all elements in the code.

### Error: Оператор "\?\?" невозможно применить к операнду типа "(ItemContainerId)\?" и "uint"
Description of the problem: Исправляет использование оператора '??' для nullable типов ItemContainerId, добавляя свойство .Value.

- Where to look for the error: This rule analyzes directly at the point of the error.
- Regex pattern to search: $this
- How it will be fixed: $this?.Value ?? 0u
- Elements impacted by the fix: The fix applies to all elements in the code.

### Error: Оператор "==" невозможно применить к операнду типа "(uint)" и "ItemContainerId"
Description of the problem: Исправляет сравнение типа ItemContainerId с uint, используя свойство .Value.

- Where to look for the error: This rule analyzes directly at the point of the error.
- Regex pattern to search: $this == $errorGroup2
- How it will be fixed: $this.Value == $errorGroup2
- Elements impacted by the fix: The fix applies to all elements in the code.

### Error: Оператор "==" невозможно применить к операнду типа "(ItemContainerId)" и "uint"
Description of the problem: Исправляет сравнение типа ItemContainerId с uint, используя свойство .Value.

- Where to look for the error: This rule analyzes directly at the point of the error.
- Regex pattern to search: $errorGroup1 == $this
- How it will be fixed: $errorGroup1 == $this.Value
- Elements impacted by the fix: The fix applies to all elements in the code.

### Error: Не удалось найти тип или имя пространства имен "Apex"
Description of the problem: Удаляет using Apex;

- Where to look for the error: This rule analyzes the entire code.
- Regex pattern to search: using Apex;
- How it will be fixed: 
- Elements impacted by the fix: The fix applies to all elements in the code.

### Error: ".+<.+>" не содержит определения "ForEach"
Description of the problem: Добавляет using System.Linq в начало кода

- Where to look for the error: This rule analyzes the entire code.
- Regex pattern to search: $this
- How it will be fixed: using System.Linq;
$this
- Elements impacted by the fix: The fix applies to all elements in the code.

### Error: .е удается (неявно\s)?преобразовать (из|тип) "uint" в "(NetworkableId|ItemId|ItemContainerId|ulong)"
Description of the problem: Заменяет uint на ulong

- Where to look for the error: This rule analyzes the entire code.
- Regex pattern to search: (uint|UInt32)
- How it will be fixed: ulong
- Elements impacted by the fix: The fix applies to all elements in the code.

### Error: .е удается (неявно\s)?преобразовать (тип|из) "(NetworkableId|ItemId|ItemContainerId|ulong)" в "uint"
Description of the problem: Заменяет uint на ulong

- Where to look for the error: This rule analyzes the entire code.
- Regex pattern to search: (uint|UInt32)
- How it will be fixed: ulong
- Elements impacted by the fix: The fix applies to all elements in the code.

### Error: Оператор "(.{1,2})" невозможно применить к операнду типа "(NetworkableId|ItemId|ItemContainerId)\??" и "(int|ulong|uint)\??"
Description of the problem: Заменяет \.(subEntity|net??\.ID|uid) на $1.Value

- Where to look for the error: This rule analyzes directly at the point of the error.
- Regex pattern to search: \.(subEntity|net??\.ID|uid)
- How it will be fixed: $1.Value
- Elements impacted by the fix: The fix applies to all elements in the code.

### Error: Ни одна из перегрузок метода "(Factor|Test|GetWaterDepth|GetOverallWaterDepth|GetWaterInfo)" не принимает \d аргументов
Description of the problem: Добавляет false в метод класса WaterLevel

- Where to look for the error: This rule focuses on the specific line containing the error.
- Regex pattern to search: $errorGroup1\((.+)\)
- How it will be fixed: $errorGroup1($1, false)
- Elements impacted by the fix: The fix applies to all elements in the code.

### Error: Отсутствует аргумент, соответствующий требуемому параметру "(waves|volumes)" из "WaterLevel\.(Factor|Test|GetWaterDepth|GetOverallWaterDepth|GetWaterInfo)"
Description of the problem: Добавляет false в метод класса WaterLevel

- Where to look for the error: This rule focuses on the specific line containing the error.
- Regex pattern to search: $errorGroup1\((.+)\)
- How it will be fixed: $errorGroup1($1, false)
- Elements impacted by the fix: The fix applies to all elements in the code.

### Error: Отсутствует аргумент, соответствующий требуемому параметру "altMove" из ".+\.GetIdealContainer\(BasePlayer, Item, bool\)"
Description of the problem: Добавляет в метод GetIdealContainer булево true

- Where to look for the error: This rule focuses on the specific line containing the error.
- Regex pattern to search: GetIdealContainer\((.+)\)
- How it will be fixed: GetIdealContainer($1, true)
- Elements impacted by the fix: The fix applies to all elements in the code.

### Error: Невозможно присвоить значение свойству или индексатору "BasePlayer.serverInput" — доступ только для чтения
Description of the problem: Заменяет присваивание чего либо в serverInput на элементы serverInput. Например serverInput.current = serverInput1.current;

- Where to look for the error: This rule focuses on the specific line containing the error.
- Regex pattern to search: (.+)\.serverInput\s=\s(.+);
- How it will be fixed: 
        $1.serverInput.current = $2.current;
        $1.serverInput.previous = $2.previous;
         
- Elements impacted by the fix: The fix applies to all elements in the code.

### Error: "BaseRidableAnimal" не содержит определения "inventory", и не удалось найти доступный метод расширения
Description of the problem: Заменяет inventory на storageInventory для BaseRidableAnimal.

- Where to look for the error: This rule focuses on the specific line containing the error.
- Regex pattern to search: .inventory
- How it will be fixed: .storageInventory
- Elements impacted by the fix: The fix applies to all elements in the code.

### Error: "BaseProjectile.Magazine" не содержит определения "TryReload", и не удалось найти доступный метод расширения
Description of the problem: Заменяет в коде ".primaryMagazine.TryReload" на ".ServerTryReload"

- Where to look for the error: This rule focuses on the specific line containing the error.
- Regex pattern to search: .primaryMagazine.TryReload
- How it will be fixed: .ServerTryReload
- Elements impacted by the fix: The fix applies to all elements in the code.

### Error: не удается преобразовать из "ItemContainer" в "BaseEntity"
Description of the problem: inventory обычно берёться из типа который является baseEntity, значит надо взять baseEntity.inventory и подставить в TakeFrom как первый элемент.

- Where to look for the error: This rule focuses on the specific line containing the error.
- Regex pattern to search: \.TakeFrom\(([^.]+)\.inventory
- How it will be fixed: .TakeFrom($1, $1.inventory
- Elements impacted by the fix: The fix applies to all elements in the code.

### Error: "Layer" не содержит определение для "Debris"
Description of the problem: Заменяет Debris на Physics_Debris

- Where to look for the error: This rule analyzes directly at the point of the error.
- Regex pattern to search: Debris
- How it will be fixed: Physics_Debris
- Elements impacted by the fix: The fix applies to all elements in the code.

### Error: "BaseProjectile.Magazine" не содержит определения "SwitchAmmoTypesIfNeeded", и не удалось найти доступный метод расширения
Description of the problem: Удаляет primaryMagazine из кода

- Where to look for the error: This rule focuses on the specific line containing the error.
- Regex pattern to search: .primaryMagazine.
- How it will be fixed: .
- Elements impacted by the fix: The fix applies to all elements in the code.

### Error: Отсутствует аргумент, соответствующий требуемому параметру "dt" из "AutoTurret.UpdateAiming\(float\)"
Description of the problem: Если UpdateAiming не имеет параметров, то добавляет значение 1 для параметра dt.

- Where to look for the error: This rule focuses on the specific line containing the error.
- Regex pattern to search: UpdateAiming\(\)
- How it will be fixed: UpdateAiming(1)
- Elements impacted by the fix: The fix applies to all elements in the code.

### Error: не удается преобразовать из "bool" в "ItemContainer"
Description of the problem: Исправляет порядок аргументов для метода GiveItem.

- Where to look for the error: This rule focuses on the specific line containing the error.
- Regex pattern to search: (GiveItem\(.+,)(.+),([^)]+)\)
- How it will be fixed: $1$3,$2)
- Elements impacted by the fix: The fix applies to all elements in the code.

### Error: Не удается неявно преобразовать тип "ulong" в "string"
Description of the problem: Добавляет к текущему коду .ToString(), чтобы преобразовать ulong в string.

- Where to look for the error: This rule analyzes directly at the point of the error.
- Regex pattern to search: $this
- How it will be fixed: $this.ToString()
- Elements impacted by the fix: The fix applies to all elements in the code.

### Error: "KeyValuePair<ulong, ApprovedSkinInfo>" не содержит определения "(.+)", и не удалось найти доступный метод расширения
Description of the problem: Исправляет доступ к члену KeyValuePair через .Value.

- Where to look for the error: This rule focuses on the specific line containing the error.
- Regex pattern to search: (\.$errorGroup1)
- How it will be fixed: .Value$1
- Elements impacted by the fix: The fix applies to all elements in the code.

### Error: не удается преобразовать из "string" в "(NetworkableId|ItemId|ItemContainerId)"
Description of the problem: Удаляет ненужное вызов ToString() для типа, который уже является строкой.

- Where to look for the error: This rule focuses on the specific line containing the error.
- Regex pattern to search: .ToString\(\)
- How it will be fixed: 
- Elements impacted by the fix: The fix applies to all elements in the code.

### Error: Аргументы типа для метода "Array.Resize<T>\(ref T\[\], int\)" не могут определяться по использованию
Description of the problem: Удаляет вызов метода Array.Resize с неопределенным типом.

- Where to look for the error: This rule focuses on the specific line containing the error.
- Regex pattern to search: $this
- How it will be fixed: 
- Elements impacted by the fix: The fix applies to all elements in the code.

### Error: "List<.+>" не содержит определения "Length", и не удалось найти доступный метод расширения
Description of the problem: Заменяет .Length на .Count для коллекций.

- Where to look for the error: This rule focuses on the specific line containing the error.
- Regex pattern to search: \.Length
- How it will be fixed: .Count
- Elements impacted by the fix: The fix applies to all elements in the code.

### Error: Не удается неявно преобразовать тип "ListHashSet<.+>" в "System.Collections.Generic.List<(.+)>"
Description of the problem: Заменяет ListHashSet на List, используя конструктор List.

- Where to look for the error: This rule focuses on the specific line containing the error.
- Regex pattern to search: ([\d\w]+\s*=)\s*(.+);
- How it will be fixed: $1new List<{$errorGroup1}>($2);
- Elements impacted by the fix: The fix applies to all elements in the code.

### Error: Не удалось найти тип или имя пространства имен "BaseCar"
Description of the problem: Заменяет BaseCar на BasicCar.

- Where to look for the error: This rule focuses on the specific line containing the error.
- Regex pattern to search: BaseCar
- How it will be fixed: $BasicCar
- Elements impacted by the fix: The fix applies to all elements in the code.

### Error: "ListHashSet<.+>" не содержит определения "Find"
Description of the problem: Заменяет Find на FirstOrDefault для ListHashSet.

- Where to look for the error: This rule focuses on the specific line containing the error.
- Regex pattern to search: \.Find(\(.+\));
- How it will be fixed: .FirstOrDefault$1;
- Elements impacted by the fix: The fix applies to all elements in the code.

### Error: Не удалось найти тип или имя пространства имен "NPCPlayerApex"
Description of the problem: Заменяет NPCPlayerApex на BaseNpc.

- Where to look for the error: This rule analyzes the entire code.
- Regex pattern to search: NPCPlayerApex
- How it will be fixed: BaseNpc
- Elements impacted by the fix: The fix applies to all elements in the code.

### Error: "BaseBoat" не содержит определения "myRigidBody"
Description of the problem: Заменяет myRigidBody на rigidBody.

- Where to look for the error: This rule focuses on the specific line containing the error.
- Regex pattern to search: myRigidBody
- How it will be fixed: rigidBody
- Elements impacted by the fix: The fix applies to all elements in the code.

### Error: "TriggerRadiation" не содержит определения "radiationSize"
Description of the problem: Удаляет строку с ошибкой, если тип TriggerRadiation не содержит определение для radiationSize.

- Where to look for the error: This rule focuses on the specific line containing the error.
- Regex pattern to search: $this
- How it will be fixed: 
- Elements impacted by the fix: The fix applies to all elements in the code.

### Error: Не удалось найти тип или имя пространства имен "PlantEntity"
Description of the problem: Заменяет PlantEntity на GrowableEntity.

- Where to look for the error: This rule focuses on the specific line containing the error.
- Regex pattern to search: PlantEntity
- How it will be fixed: GrowableEntity
- Elements impacted by the fix: The fix applies to all elements in the code.

### Error: "ListHashSet<.+>" не содержит определения "ToArray"
Description of the problem: Добавляет System.Linq.

- Where to look for the error: This rule analyzes the entire code.
- Regex pattern to search: $this
- How it will be fixed: using System.Linq;
 $this
- Elements impacted by the fix: The fix applies to all elements in the code.

### Error: "RelationshipManager" не содержит определения "playerGangs"
Description of the problem: Заменяет playerGangs на playerToTeam.

- Where to look for the error: This rule focuses on the specific line containing the error.
- Regex pattern to search: playerGangs
- How it will be fixed: playerToTeam
- Elements impacted by the fix: The fix applies to all elements in the code.

### Error: Не удается преобразовать группу методов "Value" в тип, не являющийся делегатом "ulong". Предполагалось вызывать этот метод?
Description of the problem: Убирает лишний .Value.

- Where to look for the error: This rule focuses on the specific line containing the error.
- Regex pattern to search: \.Value\.Value
- How it will be fixed: .Value
- Elements impacted by the fix: The fix applies to all elements in the code.

### Error: "ulong" является тип, который недопустим в данном контексте
Description of the problem: Исправляет использование типа ulong.

- Where to look for the error: This rule focuses on the specific line containing the error.
- Regex pattern to search: (.+=) \(new ([\d\w]+)\(UInt64\)\)([^;]+);
- How it will be fixed: $1 new $2($3);
- Elements impacted by the fix: The fix applies to all elements in the code.

### Error: не удается преобразовать из "ulong" в "(NetworkableId|ItemId|ItemContainerId)"
Description of the problem: Удаляет лишний Value.

- Where to look for the error: This rule analyzes directly at the point of the error.
- Regex pattern to search: \.Value
- How it will be fixed: 
- Elements impacted by the fix: The fix applies to all elements in the code.

### Error: Не удалось изменить возвращаемое значение ".+.uid", т. к. оно не является переменной
Description of the problem: Исправляет присвоение значения uid.

- Where to look for the error: This rule focuses on the specific line containing the error.
- Regex pattern to search: \.uid\.Value\s*=\s*(.+);
- How it will be fixed: .uid = new NetworkableId($1);
- Elements impacted by the fix: The fix applies to all elements in the code.

### Error: Не удается преобразовать тип "System.Collections.Generic.KeyValuePair<.+, BaseNetworkable>" в "System.Collections.Generic.KeyValuePair<ulong, BaseNetworkable>"
Description of the problem: Заменяет тип на var.

- Where to look for the error: This rule focuses on the specific line containing the error.
- Regex pattern to search: KeyValuePair<.+,\s*BaseNetworkable>
- How it will be fixed: var;
- Elements impacted by the fix: The fix applies to all elements in the code.

### Error: Недопустимый термин "(.+)" в выражении
Description of the problem: Исправляет выражение с некорректным термином.

- Where to look for the error: This rule focuses on the specific line containing the error.
- Regex pattern to search: \(\({$errorGroup1}\)(.+)\)
- How it will be fixed: ($1)
- Elements impacted by the fix: The fix applies to all elements in the code.

### Error: Ни одна из перегрузок метода "Add" не принимает 2 аргументов
Description of the problem: Исправляет вызов метода Add с неправильным количеством аргументов.

- Where to look for the error: This rule focuses on the specific line containing the error.
- Regex pattern to search: Add\((.+),.+\)
- How it will be fixed: Add($1)
- Elements impacted by the fix: The fix applies to all elements in the code.

### Error: "MotorRowboat" не содержит определения "dying"
Description of the problem: Заменяет .dying. на .IsDying.

- Where to look for the error: This rule focuses on the specific line containing the error.
- Regex pattern to search: .dying.
- How it will be fixed: .IsDying
- Elements impacted by the fix: The fix applies to all elements in the code.

### Error: "ulong" не содержит определения "Value"
Description of the problem: Удаляет .Value.

- Where to look for the error: This rule focuses on the specific line containing the error.
- Regex pattern to search: (^|\s)ID\.Value
- How it will be fixed: ID
- Elements impacted by the fix: The fix applies to all elements in the code.

### Error: "TrainEngine" не содержит определения "decayDuration"
Description of the problem: Заменяет .decayDuration на .decayingFor.

- Where to look for the error: This rule focuses on the specific line containing the error.
- Regex pattern to search: \.decayDuration
- How it will be fixed: .decayingFor
- Elements impacted by the fix: The fix applies to all elements in the code.

### Error: "JunkPile" не содержит определения "PlayersNearby"
Description of the problem: Удаляет PlayersNearby.

- Where to look for the error: This rule focuses on the specific line containing the error.
- Regex pattern to search: .*PlayersNearby.*
- How it will be fixed: 
- Elements impacted by the fix: The fix applies to all elements in the code.

### Error: .е удается (неявно\s)?преобразовать (из|тип) "BaseHelicopter" в "PatrolHelicopter"
Description of the problem: Заменяет BaseHelicopter на PatrolHelicopter.

- Where to look for the error: This rule focuses on the specific line containing the error.
- Regex pattern to search: BaseHelicopter
- How it will be fixed: PatrolHelicopter
- Elements impacted by the fix: The fix applies to all elements in the code.

### Error: "Minicopter" является тип, который недопустим в данном контексте
Description of the problem: Заменяет "Minicopter" на "MiniCopter".

- Where to look for the error: This rule focuses on the specific line containing the error.
- Regex pattern to search: (Minicopter,
- How it will be fixed: (MiniCopter,
- Elements impacted by the fix: The fix applies to all elements in the code.

### Error: "Имя "Net" не существует в текущем контексте
Description of the problem: Заменяет "Net.sv" на "Network.Net.sv".

- Where to look for the error: This rule focuses on the specific line containing the error.
- Regex pattern to search: (?<!Network\.)Net\.sv
- How it will be fixed: Network.Net.sv
- Elements impacted by the fix: The fix applies to all elements in the code.

### Error: Ни одна из перегрузок метода "CanMoveTo" не принимает 3 аргументов
Description of the problem: Исправляет вызов метода CanMoveTo с неправильным количеством аргументов.

- Where to look for the error: This rule focuses on the specific line containing the error.
- Regex pattern to search: (\.CanMoveTo\([^,)]+,[^,)]+),[^,)]+\)
- How it will be fixed: $1)
- Elements impacted by the fix: The fix applies to all elements in the code.

### Error: "Minicopter" не содержит определения "waterSample"
Description of the problem: Заменяет waterSample на engineController.waterloggedPoint для Minicopter.

- Where to look for the error: This rule focuses on the specific line containing the error.
- Regex pattern to search: \.waterSample\.
- How it will be fixed: .engineController.waterloggedPoint.
- Elements impacted by the fix: The fix applies to all elements in the code.

### Error: "SupplyDrop" не содержит определения "parachute"
Description of the problem: Заменяет parachute на ParachuteRoot.ToBaseEntity() для SupplyDrop.

- Where to look for the error: This rule focuses on the specific line containing the error.
- Regex pattern to search: \.parachute
- How it will be fixed: .ParachuteRoot.ToBaseEntity()
- Elements impacted by the fix: The fix applies to all elements in the code.

### Error: "BaseProjectile.Magazine" не содержит определения "Reload"
Description of the problem: Заменяет Reload на TryReload для BaseProjectile.Magazine.

- Where to look for the error: This rule focuses on the specific line containing the error.
- Regex pattern to search: \.Reload
- How it will be fixed: .TryReload
- Elements impacted by the fix: The fix applies to all elements in the code.

### Error: Не удается неявно преобразовать тип "PatrolHelicopter" в "BaseHelicopter"
Description of the problem: Заменяет BaseHelicopter на PatrolHelicopter.

- Where to look for the error: This rule focuses on the specific line containing the error.
- Regex pattern to search: BaseHelicopter
- How it will be fixed: PatrolHelicopter
- Elements impacted by the fix: The fix applies to all elements in the code.

### Error: "BaseHelicopter" не содержит определения ".+", и не удалось найти доступный метод расширения
Description of the problem: Заменяет BaseHelicopter на PatrolHelicopter.

- Where to look for the error: This rule analyzes the entire code.
- Regex pattern to search: BaseHelicopter
- How it will be fixed: PatrolHelicopter
- Elements impacted by the fix: The fix applies to all elements in the code.

### Error: Не удается неявно преобразовать тип ".+<(NetworkableId|ItemId|ItemContainerId)>" в ".+<(uint|ulong)>"
Description of the problem: Заменяет .net.ID на .net.ID.Value.

- Where to look for the error: This rule analyzes directly at the point of the error.
- Regex pattern to search: \.net\.ID
- How it will be fixed: .net.ID.Value
- Elements impacted by the fix: The fix applies to all elements in the code.

### Error: Отсутствует аргумент, соответствующий требуемому параметру "yOffset" из "BaseNavigator.PlaceOnNavMesh\(float\)"
Description of the problem: Добавляет значение по умолчанию 0f для параметра yOffset в вызов метода PlaceOnNavMesh.

- Where to look for the error: This rule focuses on the specific line containing the error.
- Regex pattern to search: PlaceOnNavMesh\(\)
- How it will be fixed: PlaceOnNavMesh(0f)
- Elements impacted by the fix: The fix applies only to methods.

### Error: не удается преобразовать из "GameObjectRef" в "UnityEngine.GameObject"
Description of the problem: Добавляет вызов метода Get() к переменной типа GameObjectRef в месте возникновения ошибки.

- Where to look for the error: This rule analyzes directly at the point of the error.
- Regex pattern to search: $this
- How it will be fixed: $this.Get()
- Elements impacted by the fix: The fix applies only to methods.

### Error: Не удается неявно преобразовать тип "System.Collections.Generic.List<ProtoBuf.PlayerNameID>" в "System.Collections.Generic.HashSet<ProtoBuf.PlayerNameID>"
Description of the problem: Replaces ToList() with ToHashSet() to correct collection conversion from List to HashSet.

- Where to look for the error: This rule focuses on the specific line containing the error.
- Regex pattern to search: \.ToList\(\)
- How it will be fixed: .ToHashSet()
- Elements impacted by the fix: The fix applies to all elements in the code.

### Error: "ConstructionGrade" не содержит определения "costToBuild"
Description of the problem: Заменяет вызов переменной costToBuild на вызов метода CostToBuild() для исправления ошибки отсутствия метода.

- Where to look for the error: This rule focuses on the specific line containing the error.
- Regex pattern to search: \.costToBuild
- How it will be fixed: .CostToBuild()
- Elements impacted by the fix: The fix applies to all elements in the code.

### Error: Не удается неявно преобразовать тип "ItemId" в "ulong"
Description of the problem: Добавляет .Value для исправления ошибки неявного преобразования ItemId в ulong.

- Where to look for the error: This rule focuses on the specific line containing the error.
- Regex pattern to search: (\.uid)
- How it will be fixed: .uid.Value
- Elements impacted by the fix: The fix applies to all elements in the code.

### Error: "HitInfo" не содержит определения "Weaponnet"
Description of the problem: Заменяет ошибочный вызов "Weaponnet" на корректный вызов "Weapon.net.ID.Value".

- Where to look for the error: This rule focuses on the specific line containing the error.
- Regex pattern to search: (info\.Weaponnet)
- How it will be fixed: info.Weapon.net
- Elements impacted by the fix: The fix applies to all elements in the code.

### Error: Не удалось найти тип или имя пространства имен "MiniCopter"
Description of the problem: Заменяет MiniCopter на PlayerHelicopter в строке с ошибкой

- Where to look for the error: This rule focuses on the specific line containing the error.
- Regex pattern to search: MiniCopter
- How it will be fixed: PlayerHelicopter
- Elements impacted by the fix: The fix applies to all elements in the code.

### Error: "MiniCopter" не существует в текущем контексте
Description of the problem: Исправляет контекст использования MiniCopter

- Where to look for the error: This rule focuses on the specific line containing the error.
- Regex pattern to search: MiniCopter
- How it will be fixed: Minicopter
- Elements impacted by the fix: The fix applies to all elements in the code.

### Error: "Minicopter" не содержит определения "waterSample", и не удалось найти доступный метод расширения "waterSample", принимающий тип "Minicopter"
Description of the problem: Заменяет waterSample на engineController.waterloggedPoint

- Where to look for the error: This rule focuses on the specific line containing the error.
- Regex pattern to search: \.waterSample\.
- How it will be fixed: .engineController.waterloggedPoint.
- Elements impacted by the fix: The fix applies to all elements in the code.

### Error: "Minicopter" является тип, который недопустим в данном контексте
Description of the problem: Заменяет Minicopter на MiniCopter в контексте использования

- Where to look for the error: This rule focuses on the specific line containing the error.
- Regex pattern to search: (Minicopter,)
- How it will be fixed: (MiniCopter,)
- Elements impacted by the fix: The fix applies to all elements in the code.

### Error: Оператор "==" невозможно применить к операнду типа "ulong" и "NetworkableId"
Description of the problem: Заменяет .net.ID на .net.ID.Value для правильного сравнения с ulong.

- Where to look for the error: This rule focuses on the specific line containing the error.
- Regex pattern to search: \.net\.ID
- How it will be fixed: .net.ID.Value
- Elements impacted by the fix: The fix applies to all elements in the code.

### Error: Не удается преобразовать из "NetworkableId" в "ulong"
Description of the problem: Заменяет .net.ID на .net.ID.Value для корректного преобразования NetworkableId в ulong.

- Where to look for the error: This rule focuses on the specific line containing the error.
- Regex pattern to search: \.net\.ID
- How it will be fixed: .net.ID.Value
- Elements impacted by the fix: The fix applies to all elements in the code.

### Error: "BaseVehicleSeat" не содержит определения "GetVehicleParent", и не удалось найти доступный метод расширения "GetVehicleParent"
Description of the problem: Заменяет вызов GetVehicleParent() на VehicleParent() для класса BaseVehicleSeat.

- Where to look for the error: This rule focuses on the specific line containing the error.
- Regex pattern to search: GetVehicleParent\(\)
- How it will be fixed: VehicleParent()
- Elements impacted by the fix: The fix applies to all elements in the code.

### Error: "BaseVehicleMountPoint" не содержит определения "GetVehicleParent", и не удалось найти доступный метод расширения "GetVehicleParent"
Description of the problem: Заменяет вызов GetVehicleParent() на VehicleParent() для класса BaseVehicleMountPoint.

- Where to look for the error: This rule focuses on the specific line containing the error.
- Regex pattern to search: GetVehicleParent\(\)
- How it will be fixed: VehicleParent()
- Elements impacted by the fix: The fix applies to all elements in the code.

### Error: не удается преобразовать из "NetworkableId" в "ulong"
Description of the problem: Заменяет .net.ID на .net.ID.Value для правильного преобразования NetworkableId в ulong.

- Where to look for the error: This rule focuses on the specific line containing the error.
- Regex pattern to search: \.net\.ID
- How it will be fixed: .net.ID.Value
- Elements impacted by the fix: The fix applies to all elements in the code.

### Error: "IFuelSystem" не содержит определения "GetFuelContainer"
Description of the problem: Исправляет вызов GetFuelSystem для корректного приведения к EntityFuelSystem.

- Where to look for the error: This rule focuses on the specific line containing the error.
- Regex pattern to search: GetFuelSystem\(\)
- How it will be fixed: (minicopter.GetFuelSystem() as EntityFuelSystem)?.GetFuelContainer()
- Elements impacted by the fix: The fix applies to all elements in the code.

### Error: "IFuelSystem" не содержит определения "GetFuelContainer"
Description of the problem: Исправляет вызов GetFuelSystem и GetFuelContainer для правильного приведения типов.

- Where to look for the error: This rule focuses on the specific line containing the error.
- Regex pattern to search: ([\w\d]+)\.GetFuelSystem\(\)\.GetFuelContainer\(\)
- How it will be fixed: ($1.GetFuelSystem() as EntityFuelSystem)?.GetFuelContainer()
- Elements impacted by the fix: The fix applies to all elements in the code.

### Error: Требуется идентификатор
Description of the problem: Удаляет начальную приставку которая вызывает ошибку

- Where to look for the error: This rule focuses on the specific line containing the error.
- Regex pattern to search: [\w\d]+\.(\(.+\)\??.+)
- How it will be fixed: $1
- Elements impacted by the fix: The fix applies to all elements in the code.

### Error: "StorageContainer" не содержит определения "GetFuelContainer"
Description of the problem: Удаляет лишний вызов метода GetFuelContainer.

- Where to look for the error: This rule focuses on the specific line containing the error.
- Regex pattern to search: \.GetFuelContainer\(\)\.GetFuelContainer\(\)
- How it will be fixed: .GetFuelContainer()
- Elements impacted by the fix: The fix applies to all elements in the code.

### Error: "RelationshipManager" не содержит определение для "(Instance|_instance)"
Description of the problem: Заменяет RelationshipManager.Instance на RelationshipManager.ServerInstance.

- Where to look for the error: This rule focuses on the specific line containing the error.
- Regex pattern to search: RelationshipManager\.$errorGroup1
- How it will be fixed: RelationshipManager.ServerInstance
- Elements impacted by the fix: The fix applies to all elements in the code.

### Error: "PlayerInventory" не содержит определения "FindItemIDs", и не удалось найти доступный метод расширения "FindItemIDs", принимающий тип "PlayerInventory" в качестве первого аргумента
Description of the problem: Заменяет вызов метода FindItemIDs на FindItemsByItemID в классе PlayerInventory.

- Where to look for the error: This rule focuses on the specific line containing the error.
- Regex pattern to search: FindItemIDs
- How it will be fixed: FindItemsByItemID
- Elements impacted by the fix: The fix applies to all elements in the code.

### Error: "PlayerInventory" не содержит определения "FindItemID", и не удалось найти доступный метод расширения "FindItemID", принимающий тип "PlayerInventory" в качестве первого аргумента
Description of the problem: Заменяет вызов метода FindItemID на FindItemByItemID в классе PlayerInventory.

- Where to look for the error: Unknown analyze type
- Regex pattern to search: FindItemID
- How it will be fixed: FindItemByItemID
- Elements impacted by the fix: The fix applies to all elements in the code.

### Error: "BasePlayer" не содержит определения "EnableServerFall"
Description of the problem: Заменяет вызовы EnableServerFall на SetServerFall у BasePlayer.

- Where to look for the error: This rule focuses on the specific line containing the error.
- Regex pattern to search: \.EnableServerFall\((\w+)\);
- How it will be fixed: .SetServerFall($1);
- Elements impacted by the fix: The fix applies to all elements in the code.

### Error: "Recycler" не содержит определения "dropChance", и не удалось найти доступный метод расширения "dropChance", принимающий тип "Recycler" в качестве первого аргумента
Description of the problem: Удаляет вызов dropChance для Recycler.

- Where to look for the error: This rule focuses on the specific line containing the error.
- Regex pattern to search: .+dropChance\s=.+;
- How it will be fixed: 
- Elements impacted by the fix: The fix applies to all elements in the code.

### Error: "StorageContainer" не содержит определения "dropChance", и не удалось найти доступный метод расширения "dropChance"
Description of the problem: Удаляет вызов dropChance для StorageContainer.

- Where to look for the error: This rule focuses on the specific line containing the error.
- Regex pattern to search: ,?\s*[\d\w.]+\.dropChance
- How it will be fixed: 
- Elements impacted by the fix: The fix applies to all elements in the code.

### Error: ".+<.+>" не содержит определения "ForEach"
Description of the problem: Добавляет ToList() перед вызовом ForEach у ListHashSet<BasePlayer>.

- Where to look for the error: This rule analyzes directly at the point of the error.
- Regex pattern to search: $this
- How it will be fixed: ToList().$this
- Elements impacted by the fix: The fix applies to all elements in the code.

### Error: Не удается преобразовать тип "ItemContainerId" в "int"
Description of the problem: Заменяет приведение ItemContainerId к int на доступ к его свойству .Value в строке 87

- Where to look for the error: This rule focuses on the specific line containing the error.
- Regex pattern to search: \((int|Int32)\)\s*([a-zA-Z0-9_]+\.uid)
- How it will be fixed: $2.Value
- Elements impacted by the fix: The fix applies to all elements in the code.

### Error: Не удается неявно преобразовать тип "ListHashSet<BasePlayer>" в "System.Collections.Generic.List<BasePlayer>".
Description of the problem: Добавляет вызов .ToList() для преобразования ListHashSet<BasePlayer> в List<BasePlayer> в строках с этой ошибкой.

- Where to look for the error: This rule analyzes only the method where the error occurs.
- Regex pattern to search: (BasePlayer\.(activePlayerList|sleepingPlayerList))
- How it will be fixed: $1.ToList()
- Elements impacted by the fix: The fix applies to all elements in the code.

### Error: Имя "nw" не существует в текущем контексте
Description of the problem: Добавляет объявление переменной NetWrite перед вызовом

- Where to look for the error: This rule focuses on the specific line containing the error.
- Regex pattern to search: if\s*\(\s*nw\s*\.Start\s*\(\)\s*\)
- How it will be fixed: NetWrite nw = Net.sv.StartWrite();

- Elements impacted by the fix: The fix applies to all elements in the code.

### Error: "Server" не содержит определения "write", и не удалось найти доступный метод расширения "write", принимающий тип "Server" в качестве первого аргумента
Description of the problem: Заменяет Net.sv.write на nw, используя новый подход с NetWrite для записи данных.

- Where to look for the error: Unknown analyze type
- Regex pattern to search: (Network\.)?Net\.sv\.write
- How it will be fixed: nw
- Elements impacted by the fix: The fix applies to all elements in the code.

### Error: "BaseMountable" не содержит определение для "FixedUpdateMountables"
Description of the problem: Заменяет FixedUpdateMountables на AllMountables в классе BaseMountable.

- Where to look for the error: This rule focuses on the specific line containing the error.
- Regex pattern to search: BaseMountable\.FixedUpdateMountables
- How it will be fixed: BaseMountable.AllMountables
- Elements impacted by the fix: The fix applies to all elements in the code.

### Error: Не удается преобразовать тип "BasePlayer.EncryptedValue<ulong>" в "long"
Description of the problem: Заменяет преобразование EncryptedValue<ulong> в long на вызов метода Get(), поддерживая любое имя переменной.

- Where to look for the error: This rule analyzes directly at the point of the error.
- Regex pattern to search: \(long\)\s*([a-zA-Z0-9_]+)\.userID
- How it will be fixed: $1.userID.Get()
- Elements impacted by the fix: The fix applies to all elements in the code.

### Error: Оператор "==" для операнда типа "long" и "ulong" является неоднозначным.
Description of the problem: Удаляет приведение к long для переменной steamID при сравнении с ulong.

- Where to look for the error: This rule analyzes directly at the point of the error.
- Regex pattern to search: \(long\)\s*([a-zA-Z0-9_]+)\.steamID
- How it will be fixed: $1.steamID
- Elements impacted by the fix: The fix applies to all elements in the code.

### Error: "RidableHorse" не содержит определения "inventory"
Description of the problem: Заменяет "inventory" на "equipmentInventory" для класса RidableHorse.

- Where to look for the error: This rule focuses on the specific line containing the error.
- Regex pattern to search: \.inventory
- How it will be fixed: .equipmentInventory
- Elements impacted by the fix: The fix applies to all elements in the code.

### Error: "BuildingBlock" не содержит определения "GetGrade", и не удалось найти доступный метод расширения "GetGrade", принимающий тип "BuildingBlock" в качестве первого аргумента
Description of the problem: Заменяет вызов GetGrade на корректный вызов через blockDefinition и skinID.

- Where to look for the error: This rule focuses on the specific line containing the error.
- Regex pattern to search: ([^\s=]+)\.GetGrade\(([^\\)]+)\).costToBuild
- How it will be fixed: $1.blockDefinition.GetGrade($2, $1.skinID).CostToBuild($2)
- Elements impacted by the fix: The fix applies to all elements in the code.

### Error: Имя "containeruid" не существует в текущем контексте
Description of the problem: Исправляет опечатку, заменяя 'containeruid' на 'container.uid'.

- Where to look for the error: This rule analyzes directly at the point of the error.
- Regex pattern to search: containeruid
- How it will be fixed: container.uid
- Elements impacted by the fix: The fix applies to all elements in the code.

### Error: не удается преобразовать из "ItemId" в "ulong"
Description of the problem: Добавляет свойство .Value для преобразования ItemId в ulong для любой переменной, соответствующей правилам именования в C#.

- Where to look for the error: This rule focuses on the specific line containing the error.
- Regex pattern to search: ([a-zA-Z_][a-zA-Z0-9_]*)\.uid
- How it will be fixed: $1.uid.Value
- Elements impacted by the fix: The fix applies to all elements in the code.

### Error: Аргумент 3: не удается преобразовать из "string\[\]" в "bool"
Description of the problem: Adds 'overlay: false' to the third argument of ShowToast method to fix the bool conversion error.

- Where to look for the error: This rule focuses on the specific line containing the error.
- Regex pattern to search: ShowToast\(([^,]+),\s*([^,]+),\s*Array\.Empty<string>\(\)\);
- How it will be fixed: ShowToast($1, $2, overlay: false, Array.Empty<string>());
- Elements impacted by the fix: The fix applies to all elements in the code.

### Error: Не удается неявно преобразовать тип "ulong" в "(NetworkableId|ItemId|ItemContainerId)"
Description of the problem: Fixes the implicit conversion from ulong to (NetworkableId|ItemId|ItemContainerId) by using the appropriate constructor.

- Where to look for the error: This rule analyzes directly at the point of the error.
- Regex pattern to search: $this
- How it will be fixed: new $errorGroup1($this)
- Elements impacted by the fix: The fix applies to all elements in the code.

### Error: Не удается неявно преобразовать тип "BasePlayer.EncryptedValue<ulong>" в "string".
Description of the problem: Converts BasePlayer.EncryptedValue<ulong> to string by calling the ToString() method to fix the implicit conversion error.

- Where to look for the error: This rule analyzes directly at the point of the error.
- Regex pattern to search: $this
- How it will be fixed: $this.ToString()
- Elements impacted by the fix: The fix applies to all elements in the code.

### Error: Не удается неявно преобразовать тип "IFuelSystem" в "(\w+)".
Description of the problem: Fixes the implicit conversion error by applying an explicit type cast using the 'as' keyword to convert IFuelSystem to the appropriate type.

- Where to look for the error: This rule analyzes directly at the point of the error.
- Regex pattern to search: $this
- How it will be fixed: $this as $errorGroup1
- Elements impacted by the fix: The fix applies to all elements in the code.

### Error: не удается преобразовать из "(BasePlayer|NPCPlayer)" в "IAmmoContainer"
Description of the problem: Исправляет преобразование BasePlayer или NPCPlayer в IAmmoContainer путем добавления обращения к inventory для primaryMagazine.

- Where to look for the error: This rule focuses on the specific line containing the error.
- Regex pattern to search: (primaryMagazine.+\([^\s]+)\)
- How it will be fixed: $1.inventory)
- Elements impacted by the fix: The fix applies to all elements in the code.

### Error: Отсутствует аргумент, соответствующий требуемому параметру "slackLevel" из "AdvancedChristmasLights.AddPoint\(Vector3, Vector3, float\)"
Description of the problem: Добавляет недостающий аргумент slackLevel (по умолчанию 0f) для метода AddPoint.

- Where to look for the error: This rule focuses on the specific line containing the error.
- Regex pattern to search: AddPoint\(([^,]+),\s*([^,]+)\)
- How it will be fixed: AddPoint($1, $2, 0f)
- Elements impacted by the fix: The fix applies to all elements in the code.

### Error: Имя "pnet" не существует в текущем контексте.
Description of the problem: Ошибка возникает, когда в коде используется переменная или объект с именем 'pnet', которая не была объявлена или доступна в текущем контексте. Регулярное выражение заменяет 'pnet' на правильное 'p.net', чтобы исправить ошибку.

- Where to look for the error: This rule focuses on the specific line containing the error.
- Regex pattern to search: pnet
- How it will be fixed: p.net
- Elements impacted by the fix: The fix applies to all elements in the code.

### Error: Не удалось найти тип или имя пространства имен "HarmonyInstance"
Description of the problem: Заменяет 'HarmonyInstance' на 'Harmony' в коде.

- Where to look for the error: This rule analyzes directly at the point of the error.
- Regex pattern to search: HarmonyInstance
- How it will be fixed: Harmony
- Elements impacted by the fix: The fix applies to all elements in the code.

### Error: Для нестатического поля, метода или свойства "CSPlugin.HarmonyInstance" требуется ссылка на объект.
Description of the problem: Заменяет 'HarmonyInstance' на 'Harmony' в коде.

- Where to look for the error: This rule analyzes directly at the point of the error.
- Regex pattern to search: HarmonyInstance
- How it will be fixed: Harmony
- Elements impacted by the fix: The fix applies to all elements in the code.

### Error: Не удалось найти тип или имя пространства имен "Harmony"
Description of the problem: Заменяет 'using Harmony;' на 'using HarmonyLib;' во всем коде.

- Where to look for the error: This rule analyzes the entire code.
- Regex pattern to search: using Harmony;
- How it will be fixed: using HarmonyLib;
- Elements impacted by the fix: The fix applies to all elements in the code.

### Error: "Harmony" не содержит определение для "Create"
Description of the problem: Заменяет вызов 'Harmony.Create(' на 'new Harmony(' в коде.

- Where to look for the error: This rule focuses on the specific line containing the error.
- Regex pattern to search: Harmony\.Create\(
- How it will be fixed: new Harmony(
- Elements impacted by the fix: The fix applies to all elements in the code.

### Error: Оператор foreach не работает с переменными типа "HiddenValue<ListDictionary<NetworkableId, BaseNetworkable>>", так как "HiddenValue<ListDictionary<NetworkableId, BaseNetworkable>>" не содержит открытое определение экземпляра или расширения для "GetEnumerator"
Description of the problem: Исправляет использование foreach для HiddenValue<ListDictionary<NetworkableId, BaseNetworkable>>, добавляя вызов метода Get().

- Where to look for the error: This rule analyzes directly at the point of the error.
- Regex pattern to search: $this
- How it will be fixed: $this.Get()
- Elements impacted by the fix: The fix applies to all elements in the code.

### Error: Тип или имя пространства имен "Sensation" не существует в пространстве имен "Rust.Ai"
Description of the problem: Удаляет блок кода, связанный с Rust.Ai.Sensation.

- Where to look for the error: This rule analyzes only the method where the error occurs.
- Regex pattern to search: Rust\.Ai\.Sensation\s+sensation\s*=\s*new\s+Rust\.Ai\.Sensation\(\)\s*\{\s*[\s\S\r\n]*?\}
- How it will be fixed: 
- Elements impacted by the fix: The fix applies to all elements in the code.

### Error: Тип или имя пространства имен "Sense" не существует в пространстве имен "Rust.Ai"
Description of the problem: Удаляет упоминание о Rust.Ai.Sense.

- Where to look for the error: This rule focuses on the specific line containing the error.
- Regex pattern to search: $this
- How it will be fixed: 
- Elements impacted by the fix: The fix applies to all elements in the code.

### Error: Отсутствует закрывающий разделитель "}" для интерполированного выражения, начинающегося с "{".
Description of the problem: Исправляет отсутствие закрывающей скобки для тернарных операторов в интерполированных строках, добавляя круглые скобки вокруг тернарных выражений.

- Where to look for the error: This rule focuses on the specific line containing the error.
- Regex pattern to search: (\$".*\{)([^{(]+\?[^{}]+\:[^{}]+)(\}.*")
- How it will be fixed: $1($2)$3
- Elements impacted by the fix: The fix applies to all elements in the code.

### Error: "HashSet<.*>" не содержит определения "Exists", и не удалось найти доступный метод расширения "Exists", принимающий тип "HashSet<.*>" в качестве первого аргумента.
Description of the problem: Исправляет вызов метода Exists для HashSet, преобразуя его в List с использованием метода ToList().

- Where to look for the error: This rule analyzes directly at the point of the error.
- Regex pattern to search: $this
- How it will be fixed: ToList().$this
- Elements impacted by the fix: The fix applies to all elements in the code.

### Error: Имя "nw" не существует в текущем контексте
Description of the problem: Добавляет объявление и инициализацию переменной NetWrite перед её использованием в вызове nw.Start().

- Where to look for the error: This rule focuses on the specific line containing the error.
- Regex pattern to search: nw\.Start\(\);
- How it will be fixed: NetWrite nw = Network.Net.sv.StartWrite();
- Elements impacted by the fix: The fix applies to all elements in the code.

### Error: "BaseMountable" не содержит определения "needsVehicleTick", и не удалось найти доступный метод расширения "needsVehicleTick", принимающий тип "BaseMountable"
Description of the problem: Replaces 'needsVehicleTick' with 'isMobile' in the BaseMountable class.

- Where to look for the error: This rule analyzes directly at the point of the error.
- Regex pattern to search: \bneedsVehicleTick\b
- How it will be fixed: isMobile
- Elements impacted by the fix: The fix applies to all elements in the code.

### Error: не удается преобразовать из "NetworkableId" в "float"
Description of the problem: Добавляет .Value для преобразования NetworkableId в float.

- Where to look for the error: This rule analyzes directly at the point of the error.
- Regex pattern to search: $this
- How it will be fixed: $this.Value
- Elements impacted by the fix: The fix applies to all elements in the code.

### Error: "IFuelSystem" не содержит определения "([\w\d]+)"
Description of the problem: Исправляет вызов GetFuelSystem для корректного приведения к EntityFuelSystem и добавляет настройку (isServer|editorGiveFreeFuel|fuelStorageID|fuelStorageInstance|nextFuelCheckTime|cachedHasFuel|pendingFuel).

- Where to look for the error: This rule focuses on the specific line containing the error.
- Regex pattern to search: ([a-zA-Z_][^\s]*\.GetFuelSystem\(\)).($errorGroup1)
- How it will be fixed: ($1 as EntityFuelSystem).$2
- Elements impacted by the fix: The fix applies to all elements in the code.

### Error: "EntityRef<ElevatorLift>" не содержит определения "([\w\d]+)"
Description of the problem: Исправляет вызов transform для EntityRef<ElevatorLift>, добавляя вызов Get(true).

- Where to look for the error: This rule analyzes directly at the point of the error.
- Regex pattern to search: $this
- How it will be fixed: Get(true).$this
- Elements impacted by the fix: The fix applies to all elements in the code.

### Error: "EntityRef<ElevatorLift>" не содержит определение для "([\w\d]+)"
Description of the problem: Исправляет вызов transform для EntityRef<ElevatorLift>, добавляя вызов Get(true).

- Where to look for the error: This rule analyzes directly at the point of the error.
- Regex pattern to search: $this
- How it will be fixed: $this.Get(true)
- Elements impacted by the fix: The fix applies to all elements in the code.

### Error: Отсутствует аргумент, соответствующий требуемому параметру "targetPlayerId" из "BuildingPrivlidge.AddPlayer\(BasePlayer, ulong\)"
Description of the problem: Добавляет второй аргумент 'userID' в вызов метода AddPlayer(BasePlayer, ulong).

- Where to look for the error: This rule focuses on the specific line containing the error.
- Regex pattern to search: AddPlayer\(([^,]+)\);
- How it will be fixed: AddPlayer($1, $1.userID);
- Elements impacted by the fix: The fix applies to all elements in the code.

### Error: "[\d\w]+" не содержит определения "MountObject"
Description of the problem: Заменяет вызовы MountObject на SetMounted.

- Where to look for the error: This rule analyzes directly at the point of the error.
- Regex pattern to search: $this
- How it will be fixed: SetMounted
- Elements impacted by the fix: The fix applies to all elements in the code.

### Error: "PlayerInventory" не содержит определения "AllItems", и не удалось найти доступный метод расширения "AllItems", принимающий тип "PlayerInventory" в качестве первого аргумента
Description of the problem: Заменяет вызов метода AllItems на прямую работу с контейнерами inventory (containerMain, containerBelt и containerWear), а также добавляет получение имени игрока через $1.displayName.

- Where to look for the error: This rule focuses on the specific line containing the error.
- Regex pattern to search: ([\w\d]+)\??\.inventory\.AllItems\(\)
- How it will be fixed: Enumerable.Concat($1.inventory.containerMain?.itemList ?? Enumerable.Empty<Item>(), Enumerable.Concat($1.inventory.containerBelt?.itemList ?? Enumerable.Empty<Item>(), $1.inventory.containerWear?.itemList ?? Enumerable.Empty<Item>()))
- Elements impacted by the fix: The fix applies to all elements in the code.

### Error: Не удается преобразовать значение NULL в "Construction.Placement"
Description of the problem: Добавляет ? для преобразования типа "Construction.Placement" в nullable, чтобы разрешить NULL значения.

- Where to look for the error: This rule analyzes the entire code.
- Regex pattern to search: Construction\.Placement(?!\?)
- How it will be fixed: Construction.Placement?
- Elements impacted by the fix: The fix applies to all elements in the code.

### Error: "Construction.Placement\?" не содержит определения "([\d\w]+)"
Description of the problem: Добавляет .Value перед вызовом свойства "position" для nullable типа "Construction.Placement?".

- Where to look for the error: This rule focuses on the specific line containing the error.
- Regex pattern to search: ([^\s]+\s=\s?[^=\s]+)($errorGroup1)
- How it will be fixed: $1Value.$2
- Elements impacted by the fix: The fix applies to all elements in the code.

### Error: "Construction.Placement\?" не содержит определения "[\d\w]+"
Description of the problem: Добавляет .Value перед вызовом свойства "position" для nullable типа "Construction.Placement?".

- Where to look for the error: This rule analyzes directly at the point of the error.
- Regex pattern to search: $this
- How it will be fixed: Value.$this
- Elements impacted by the fix: The fix applies to all elements in the code.

### Error: Аргумент 1 должен передаваться с ключевым словом "ref".
Description of the problem: Заменяет вызов метода ModifyPlacement с передачей аргумента по ссылке на код с промежуточной переменной для корректной обработки nullable типа.

- Where to look for the error: This rule focuses on the specific line containing the error.
- Regex pattern to search: (.+\.ModifyPlacement\()([^()]+)(\);.*)
- How it will be fixed: Construction.Placement test1 = $2.Value; $1ref test1 $3 
$2 = test1;
- Elements impacted by the fix: The fix applies to all elements in the code.

### Error: "IEnumerable<Item>" не содержит определения "Length"
Description of the problem: Заменяет вызов свойства Length на метод Count() для исправления ошибки в IEnumerable<Item>, так как для IEnumerable свойство Length не доступно, а Count() из System.Linq предоставляет корректный способ получения количества элементов.

- Where to look for the error: This rule analyzes directly at the point of the error.
- Regex pattern to search: $this
- How it will be fixed: Count()
- Elements impacted by the fix: The fix applies to all elements in the code.

### Error: "PlayerInventory" не содержит определения "AllItemsNoAlloc"
Description of the problem: Заменяет вызов несуществующего метода AllItemsNoAlloc на GetAllItems для PlayerInventory, чтобы исправить ошибку отсутствия метода расширения.

- Where to look for the error: This rule analyzes directly at the point of the error.
- Regex pattern to search: $this
- How it will be fixed: GetAllItems
- Elements impacted by the fix: The fix applies to all elements in the code.

### Error: Аргумент "1" не должен передаваться с ключевым словом "ref"
Description of the problem: Удаляет ключевое слово 'ref' из вызова метода GetAllItems, так как оно не должно использоваться для первого аргумента.

- Where to look for the error: This rule focuses on the specific line containing the error.
- Regex pattern to search: \.GetAllItems\(ref\s
- How it will be fixed: .GetAllItems(
- Elements impacted by the fix: The fix applies to all elements in the code.

### Error: Невозможно присвоить значение свойству или индексатору "StorageContainer.inventory" — доступ только для чтения
Description of the problem: Заменяет свойство 'inventory', которое доступно только для чтения, на '_inventory', которое, вероятно, поддерживает запись для StorageContainer.

- Where to look for the error: This rule analyzes directly at the point of the error.
- Regex pattern to search: \.inventory
- How it will be fixed: ._inventory
- Elements impacted by the fix: The fix applies to all elements in the code.

### Error: Имя "Enumerable" не существует в текущем контексте
Description of the problem: Добавляет директиву using System.Linq в начало файла для использования методов расширения из класса Enumerable.

- Where to look for the error: This rule analyzes the entire code.
- Regex pattern to search: $this
- How it will be fixed: using Enumerable = System.Linq.Enumerable;
$this
- Elements impacted by the fix: The fix applies to all elements in the code.

### Error: Ни одна из перегрузок метода "CancelAll" не принимает 1 аргументов.
Description of the problem: Исправляет вызов метода CancelAll с одним аргументом, удаляя лишние параметры и оставляя пустые скобки.

- Where to look for the error: This rule focuses on the specific line containing the error.
- Regex pattern to search: CancelAll\([^()]+\)
- How it will be fixed: CancelAll()
- Elements impacted by the fix: The fix applies to all elements in the code.

### Error: Отсутствует аргумент, соответствующий требуемому параметру "side" из "BuildingBlock.RemoveWallpaper\(int\)".
Description of the problem: Добавляет аргумент 'side' в вызов метода RemoveWallpaper у объекта BuildingBlock.

- Where to look for the error: This rule focuses on the specific line containing the error.
- Regex pattern to search: RemoveWallpaper\(\)
- How it will be fixed: RemoveWallpaper(0)
- Elements impacted by the fix: The fix applies to all elements in the code.

### Error: "StartSpawnPlayerHelicopter" не существует в текущем контексте
Description of the problem: Заменяет вызов 'StartSpawnPlayerHelicopter' на 'StartSpawnMiniCopter'.

- Where to look for the error: This rule analyzes directly at the point of the error.
- Regex pattern to search: $this
- How it will be fixed: StartSpawnMiniCopter
- Elements impacted by the fix: The fix applies to all elements in the code.

### Error: Псевдоним using "Enumerable" ранее встречался в этом пространстве имен.
Description of the problem: Удаляет лишние using Enumerable = System.Linq.Enumerable;

- Where to look for the error: This rule analyzes the entire code.
- Regex pattern to search: using Enumerable = System.Linq.Enumerable;
??\s?using Enumerable = System.Linq.Enumerable;
- How it will be fixed: using Enumerable = System.Linq.Enumerable;
- Elements impacted by the fix: The fix applies to all elements in the code.

### Error: "WaterSystem" не содержит определение для "GetHeight"
Description of the problem: Заменяет вызов WaterSystem.GetHeight на условное выражение, проверяющее наличие WaterSystem.Instance и корректно использующее oceanSimulation.GetHeight.

- Where to look for the error: This rule focuses on the specific line containing the error.
- Regex pattern to search: WaterSystem\.GetHeight\(([^)]+)\)
- How it will be fixed: WaterSystem.Instance == null ? WaterSystem.OceanLevel : WaterSystem.Instance.oceanSimulation.GetHeight($1) + WaterSystem.OceanLevel
- Elements impacted by the fix: The fix applies to all elements in the code.

### Error: не удается преобразовать из "System.Collections.Generic.IEnumerable<.+>" в ".+\[\]"
Description of the problem: Добавляет вызов метода ToArray() для преобразования IEnumerable<.+> в .+[].

- Where to look for the error: This rule analyzes directly at the point of the error.
- Regex pattern to search: $this
- How it will be fixed: Enumerable.ToArray($this)
- Elements impacted by the fix: The fix applies to all elements in the code.

### Error: "BasePlayer" не содержит определения "LastBlockColourChangeId"
Description of the problem: Заменяет вызов LastBlockColourChangeId на метод получения значения цвета блока через GetInfoInt.

- Where to look for the error: This rule focuses on the specific line containing the error.
- Regex pattern to search: \b(\w+)\.LastBlockColourChangeId
- How it will be fixed: (uint)($1.GetInfoInt("client.SelectedShippingContainerBlockColour", 0) >= 0 ? (uint)$1.GetInfoInt("client.SelectedShippingContainerBlockColour", 0) : 0U)
- Elements impacted by the fix: The fix applies to all elements in the code.

### Error: Левая часть выражения назначения должна быть переменной, свойством или индексатором
Description of the problem: Заменяет присваивание через GetInfoInt на корректный вызов SetInfo для установки цвета контейнера.

- Where to look for the error: This rule focuses on the specific line containing the error.
- Regex pattern to search: \(uint\)\((\w+)\.GetInfoInt\("client\.SelectedShippingContainerBlockColour", 0\) >= 0 \? \(uint\)\1\.GetInfoInt\("client\.SelectedShippingContainerBlockColour", 0\) : 0U\)\s*=\s*([^;]+);
- How it will be fixed: $1.SetInfo("client.SelectedShippingContainerBlockColour", $2);
- Elements impacted by the fix: The fix applies to all elements in the code.

### Error: не удается преобразовать из "uint" в "string"
Description of the problem: Добавляет вызов ToString() для преобразования uint в строку.

- Where to look for the error: This rule analyzes directly at the point of the error.
- Regex pattern to search: $this
- How it will be fixed: $this.ToString()
- Elements impacted by the fix: The fix applies to all elements in the code.

### Error: Не удается неявно преобразовать тип "System.Collections.Generic.IEnumerable<.+>" в ".+\[\]"
Description of the problem: Заменяет вызов, добавляя приведение к массиву с помощью метода ToArray.

- Where to look for the error: This rule analyzes directly at the point of the error.
- Regex pattern to search: $this
- How it will be fixed: Enumerable.ToArray($this)
- Elements impacted by the fix: The fix applies to all elements in the code.

### Error: Невызываемый член "BasePlayer.IsAdmin" не может использоваться как метод
Description of the problem: Удаляет скобки '()' при вызове IsAdmin у BasePlayer.

- Where to look for the error: This rule focuses on the specific line containing the error.
- Regex pattern to search: \.IsAdmin\(\)
- How it will be fixed: .IsAdmin
- Elements impacted by the fix: The fix applies to all elements in the code.

### Error: Невызываемый член "BasePlayer.IsConnected" не может использоваться как метод
Description of the problem: Удаляет скобки '()' при вызове IsConnected у BasePlayer.

- Where to look for the error: This rule focuses on the specific line containing the error.
- Regex pattern to search: \.IsConnected\(\)
- How it will be fixed: .IsConnected
- Elements impacted by the fix: The fix applies to all elements in the code.

### Error: "ConsoleSystem.Arg" не содержит определения "connection"
Description of the problem: Заменяет некорректное использование 'connection' на 'Connection' для типа ConsoleSystem.Arg.

- Where to look for the error: This rule analyzes directly at the point of the error.
- Regex pattern to search: $this
- How it will be fixed: Connection
- Elements impacted by the fix: The fix applies to all elements in the code.

### Error: не удается преобразовать из "System.IO.MemoryStream" в "byte\[\]"
Description of the problem: Заменяет вызов MemoryStream на вызов ToArray() для преобразования в byte[].

- Where to look for the error: This rule analyzes directly at the point of the error.
- Regex pattern to search: $this
- How it will be fixed: $this.ToArray()
- Elements impacted by the fix: The fix applies to all elements in the code.

