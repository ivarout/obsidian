
In C++ Create Godot Nodes e.g. for a RigidBody3D, which will create and add components for e.g. Position, Velocity, etc. in our ecs. When done processing all systems, we need to sync this with the actual 3d objects again.

1. Start with a RigidBody3D derived node created in C++: e.g.: ECS_RigidBody3D

For components, we can create components that are fast by implementing them in C++, or components that are slower to access by creating them in godot. When created in godot, we have to inherit from a C++ created component base class, e.g.:

``` c++
struct ScriptComponent {  
    godot::ObjectID godot_node_id;  
    // Or a Variant dictionary for custom data  
    godot::Dictionary custom_properties;  
};
```
