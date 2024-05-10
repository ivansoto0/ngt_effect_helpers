# Class: effect

## Description
The `effect` class provides a foundation for managing sound effects in a program. It serves as a base class for more specific sound effects, such as reverbs.

## Constructor
- `effect(string&in type)`
  - Initializes the effect with a specified type.
- `effect()`
  - Default constructor.

## Methods
- `bool in_range(float value, float min, float max)`
  - Checks if a value falls within a specified range (`min` to `max`, inclusive).
    - *Remarks:* Used internally to validate parameter values.
- `bool is_safe(sound@handle)`
  - Checks if a sound handle is valid and active.
    - *Remarks:* Ensures that the sound handle is usable.
- `bool attach(sound@handle)`
  - Attaches the effect to a sound handle, if safe, and configures the effect.
    - *Remarks:* Can be used to apply the effect to a regular sound object or a sound pool.
- `bool configure_effect(sound@handle)`
  - Configures the effect for a given sound handle.
    - *Remarks:* Should be overridden by derived classes to implement specific effect configurations.

## Remarks
- The `effect` class provides a foundation for implementing various sound effects.
- This class can be used with regular sound objects or the sound pool.

# Class: delay_node

## Description
The `delay_node` class represents a delay effect, which is an audio effect that repeats a sound after a certain amount of time, creating an echo-like effect. It inherits from the `effect` class.

## Constructor
- `delay_node(float dry, float wet, float decay)`
  - Initializes the delay effect with specified parameters: dryness, wetness, and decay.
- `delay_node()`
  - Default constructor. Initializes the delay effect with default parameter values.

## Methods
- `bool set_dry(float value)`
  - Sets the dry parameter of the delay effect.
- `bool set_wet(float value)`
  - Sets the wet parameter of the delay effect.
- `bool set_decay(float value)`
  - Sets the decay parameter of the delay effect.
- `bool config_from_preset(delay_node_preset@preset)`
  - Configures the delay effect based on a preset.
- `bool configure_effect(sound@handle)`
  - Configures the delay effect for a given sound handle.

## Remarks
- The `delay_node` class provides functionality for managing delay effects in audio processing.
- Parameter values should be in the range from 0.1 to 1.0.
- This class can be used with regular sound objects or the sound pool.

# Class: reverb

## Description
The `reverb` class represents a reverb effect, a type of audio effect commonly used in digital signal processing to simulate reverberation in an environment.

## Inherits from
- `effect`

## Constructor
- `reverb(float dry, float wet, float room_size, float damping, float mode)`
  - Initializes the reverb effect with specified parameters (`dry`, `wet`, `room_size`, `damping`, `mode`). Each parameter should be in the range from 0.1 to 1.0.
- `reverb()`
  - Default constructor.

## Methods
- `bool set_dry(float value)`
  - Sets the dry parameter of the reverb effect.
- `bool set_wet(float value)`
  - Sets the wet parameter of the reverb effect.
- `bool set_room_size(float value)`
  - Sets the room size parameter of the reverb effect.
- `bool set_damping(float value)`
  - Sets the damping parameter of the reverb effect.
- `bool set_mode(float value)`
  - Sets the mode parameter of the reverb effect.
- `bool config_from_preset(reverb_preset@preset)`
  - Configures the reverb effect based on a preset.
- `bool configure_effect(sound@handle)`
  - Configures the reverb effect for a given sound handle.

## Remarks
- The `reverb` class represents a specific type of audio effect used to simulate reverberation.
- It inherits from the `effect` class and provides methods to configure reverb parameters.
- This class can be used with regular sound objects or the sound pool.

# Class: effect_presets

## Description
The `effect_presets` class stores and manages presets for various sound effects.

## Properties
- `effect_presets`: A dictionary used to store effect presets.

## Methods
- `effect_preset@find_effect_preset(const string&in name)`: Finds an effect preset by name.

## Remarks
- This class allows for easy retrieval and management of effect presets.
- Presets are stored based on their names and can be accessed using the `find_effect_preset` method.

# Class: effect_preset

## Description
The `effect_preset` class represents a generic sound effect preset.

## Properties
- `name`: The name of the preset.
- `effect_type`: The type of effect associated with the preset.

## Constructor
- `effect_preset(const string&in name, int effect_type)`: Initializes the effect preset with a name and effect type.

## Remarks
- This class serves as a base class for more specific effect presets.
- Effect presets can be of different types, such as reverb or delay.

# Class: reverb_preset

## Description
The `reverb_preset` class represents a preset for a reverb effect.

## Inherits from
- `effect_preset`

## Properties
- `dry`: The dry parameter of the reverb effect.
- `wet`: The 
wet parameter of the reverb effect.
- `room_size`: The room size parameter of the reverb effect.
- `damping`: The damping parameter of the reverb effect.
- `mode`: The mode parameter of the reverb effect.

## Constructor
- `reverb_preset(string&in name, float dry, float wet, float room_size, float damping, float mode)`: Initializes the reverb preset with specified parameters.

## Remarks
- This class represents a specific preset for a reverb effect.
- It inherits properties and methods from the `effect_preset` class.

# Class: delay_node_preset

## Description
The `delay_node_preset` class represents a preset for a delay effect.

## Inherits from
- `effect_preset`

## Properties
- `dry`: The dry parameter of the delay effect.
- `wet`: The wet parameter of the delay effect.
- `decay`: The decay parameter of the delay effect.

## Constructor
- `delay_node_preset(string&in name, float dry, float wet, float decay)`: Initializes the delay preset with specified parameters.

## Remarks
- This class represents a specific preset for a delay effect.
- It inherits properties and methods from the `effect_preset` class.
