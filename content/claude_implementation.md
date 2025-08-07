
## The Key Distinction

**`new Frame()` - This should NOT be done in the SOUL framework**

When you do `new Frame()`, you're creating a **frame definition/template**, not an operational cognitive unit. This would be like creating a blueprint rather than an actual building.

**`Frame::instantiate()` → `FrameInstance` - This is the correct approach**

When you call `frame->instantiate()`, you create an independent cognitive unit that can participate in the "Society of Mind."

## Detailed Comparison

### Using `new Frame()` (Wrong Approach)

```php
// This creates a frame definition/template
$personFrame = new PersonFrame('person_001', 'Person', 'entity');

// This frame definition cannot:
// - Hold actual values in its frame elements
// - Participate in cognitive processing
// - Communicate with other agents
// - Maintain relationships with other frame instances
// - Be stored in Neo4j as a processing instance
```

### Using `Frame::instantiate()` (Correct Approach)

```php
// This creates an independent cognitive unit
$personInstance = $personFrame->instantiate(['name' => 'John', 'age' => 30]);

// This frame instance can:
// - Hold actual values (John, 30)
// - Execute agent methods
// - Communicate with other frame instances
// - Form relationships through FEs
// - Be stored in Neo4j during processing
// - Operate independently in the cognitive network
```

## Why This Distinction Matters

### 1. **Cognitive Processing**

```php
// Frame definitions are static templates
$buyFrame = new BuyFrame(); // Just a template

// Frame instances are active cognitive units
$buyInstance = $buyFrame->instantiate([
    'buyer' => $johnInstance,
    'seller' => $storeInstance,
    'goods' => $bookInstance,
    'price' => 20
]);

// Only the instance can execute the actual "buy" process
$buyInstance->executePurchase(); // This makes sense
$buyFrame->executePurchase();    // This doesn't make sense
```

### 2. **Memory and State**

```php
// Frame definitions don't hold state
$containerFrame = new ContainerFrame();
// containerFrame cannot remember what's inside it

// Frame instances hold actual state
$boxInstance = $containerFrame->instantiate();
$boxInstance->getFrameElement('contents')->setValue($appleInstance);
// Now this specific box "knows" it contains an apple
```

### 3. **Minsky's Society of Mind**

```php
// Frame definitions cannot be "agents" in the society
$frame = new ProcessFrame(); // Static definition

// Frame instances ARE the agents
$processInstance = $frame->instantiate();
// This instance can communicate with other agents:
$processInstance->sendMessageToAgent($otherInstance->getInstanceId(), 'notify', ['status' => 'complete']);
```

### 4. **Relationship Formation**

```php
// Frame definitions cannot form relationships
$frame1 = new PersonFrame();
$frame2 = new PersonFrame();
// frame1 and frame2 cannot have a relationship

// Frame instances form the actual cognitive network
$johnInstance = $personFrame->instantiate(['name' => 'John']);
$maryInstance = $personFrame->instantiate(['name' => 'Mary']);

// Now they can form relationships
$johnInstance->getFrameElement('spouse')->relateTo(
    $maryInstance->getFrameElement('identity'), 
    'MARRIED_TO'
);
```

## The Architecture Pattern

```php
// DEFINITION PHASE (happens once, usually at system startup)
class PersonFrame extends Frame {
    public function __construct() {
        parent::__construct('PERSON', 'Person Entity', 'entity');
        $this->addFrameElement(new FrameElement('name', 'string'));
        $this->addFrameElement(new FrameElement('age', 'integer'));
        $this->addFrameElement(new FrameElement('spouse', 'person'));
    }
}

// PROCESSING PHASE (happens during cognitive processing)
$personFrame = new PersonFrame(); // Template creation
$johnInstance = $personFrame->instantiate(['name' => 'John', 'age' => 30]); // Cognitive unit creation

// The Mind service manages instances, not definitions
$mindService->registerFrameInstance($johnInstance); // ✓ Correct
$mindService->registerFrameInstance($personFrame);  // ✗ Wrong
```

## Summary

- **Frame Definitions** (`new Frame()`) = Static templates/blueprints stored in code
- **Frame Instances** (`frame->instantiate()`) = Dynamic cognitive units that participate in processing

The SOUL framework's cognitive processing happens entirely through **Frame Instances**. Frame definitions are just the templates that define what kinds of cognitive units can be created.

This separation ensures that:

1. The cognitive network consists of independent, stateful units
2. Each processing context gets fresh instances
3. The system can handle multiple simultaneous cognitive processes
4. Frame definitions remain clean and reusable

Does this clarify the distinction? Would you like me to elaborate on any aspect of this design pattern?