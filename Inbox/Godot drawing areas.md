#todo 

- [ ] Check ECS implentation using Components node (containing component children), and a component bitmask for all entities.
- [ ] Check drawing areas in godot (by clicking areas on the map)
- [ ] Check Beehave for behavior Tree
- [ ] Check implementing components using groups, can we use some custom subgroup implementation, maybe by calling stuff group/subgroup
## ECS like implementation

Have an 'Entity' node with a 'Components' child node that contains all component types.

Upon component initialization, the component adds its own type to the components registry, if it's not already in the registry. Doing so will add a 'bit' to the component that is to be used in the entity bitmask. The entity bitmask can be use to very efficiently query entities with a certain set of components.

Where does all the logic live though? 