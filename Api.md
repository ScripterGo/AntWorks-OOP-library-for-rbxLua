
# Ant Class

### Constructor
*[AntClass]* **(ClassName)**

[Calls the constructor function with a newly constructed AntObject 
as one of the arguments. The return is dependant on what the set constructor function returns]

### Properties
*table* **InheritFrom**

[Is a table containing the classes currently inheriting from]
	
*string* **ClassName**

[Is a string storing the ClassName]
	
*func* **Constructor**

[Stores the constructor function for the class]

### Functions

*[AntObject]* **:Clone()**

[Returns a clone of the Object]

*[dictionary]* **:GetClassesInheritingFrom()**

[Returns a dictionary of ClassNames which is inherited from]

*[bool]* **:InheritsFrom(ClassName)**

[Returns true or false accordingly if inherits from a class with the given ClassName]

**:Inherit(AntClass,...)** 

[Takes any number of Ant Classes to inherit from]

**:DeInherit(AntClass, ...)**

[Takes any number of Ant Classes to DeInherit]

*[bool]* **:Is(ClassName)**

[Returns true if inheriting from a class with the given ClassName or if Objects Classname == ClassName]

**:SetConstruct(func, usingAntObject)**

[Sets the constructor function to the given func. usingAntObject determines if an antObject is to be created whenever .new() is called, defaults to true.]

*[Multimethod Object]* **.CreateMultimethod()**

[Creates a new multimethod objects and returns it]

# AntObject

### Constructor
*[AntObject]* **(InstantiatedBy)**

[Creates a new AntObject from the given InstantiatedBy AntClass]

### Properties

*table* **Locked[Locked]**

[Is a table were the locked indexes are stored]
	
*table* **Unlocked[Locked]**

[Is a table were the unlocked indexes are stored]
	
*table* **DataTypeLimitations[Locked]**

[Is a table containing information weather certain indexes got a datatype limitation]
	
*bool* **SuperLocked[Locked]**

[Determines if the object is superLocked]
	
*table* **InheritFrom[Locked]**

[Is a table containing every AntClass which the Ant object is inheriting from]

*AntClass* **InstantiatedFrom[Locked]**

[Is just an object value storing which AntClass the AntObject was created from]

*AntEvent* **Changed[Locked]**

[Is a custom made event that will be fired when the object is changed. Limited to changes 
of values directly in the AntObject]


### Functions

**:LockProperty(Index, ...)**

[Takes any number of indexes and makes them readOnly]
	
**:UnlockProperty(Index, ...)**

[Takes any number of indexes and removes the readOnly limitation]

**:SuperLock()**

[Locks everything, the object cannot be written to at all unless certain indexes is unlocked]

**:SuperUnlock()**

[Unlocks everything, every index in the object can now be written to]

**:LimitDataType(Index, DataType)**

[Limits the Datatype of value at Index to DataType]

**:BreakDataTypeLimit(Index)**

[Removes any Datatype limitation set to the value of Index]

*[dictionary]* **:GetClassesInheritingFrom()**

[Returns a dictionary of ClassNames which is inherited from, it will overwrite the inherited version]

**:ClearConnections()**

[Disconnects every connection connected to every event within the AntObject]

**.CreateEvent()**

[Just creates a new eventObject and returns it]

##### Inherited from AntClass

*[Object]* **:Clone()**

[Returns a clone of the Object]

*[dictionary]* **:GetClassesInheritingFrom()**

[Returns a dictionary of ClassNames which is inherited from]

*[bool]* **:InheritsFrom(ClassName)**

[Returns true or false accordingly if inherits from a class with the given ClassName]

**:Inherit(AntClass,...)**

[Takes any number of Ant Classes to inherit from]

**:DeInherit(AntClass, ...)**

[Takes any number of Ant Classes to DeInherit]

*[bool]* **:Is(ClassName)**

[Returns true if inheriting from a class with the given ClassName or if Objects Classname == ClassName]

**Note:What the AntObject inherits from is dependant on what its instantiated class inherits from**

# AntEvent

### Constructor
*[AntEvent]* **()**

[Creates a new AntEvent] 

### Properties
*bool* **Event**

[Is just an identifier]

*instance* **Bindable**

[This is the bindable event which the AntEvent is using for its core operations]

*table* **Connections**

[Is a container for every connection thats been made to the event]

### Functions

*[AntConnection]* **:Connect(func)** 

[Connects a function to be called when the event is fired]

**:Fire(...)**

[Fires of the event and there by firing every connection]

**:Wait()**

[Yields the current thread until the event is fired]

**:ClearConnections()**

[Will disconnect all connections connected to the event]

# AntConnection

### Constructor
*[AntConnection]* **(func, signal)**

[Constructs a new AntConnection with the func binded to it and signal being the 
event which the connection was connected to]

### Properties
*func* **func**

[Is the function that is binded to the connection]

*AntEvent* **Signal**

[Is the AntEvent which the connection was connected to]

### Functions
**:Disconnect()**

[Disconnects the connection from the AntEvent]


