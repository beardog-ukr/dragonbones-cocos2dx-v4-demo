# dragonbones-cocos2dx-v4-demo
This are [Dragon Bones examples](https://github.com/DragonBones/DragonBonesCPP/tree/master/Cocos2DX_3.x) ported to [cocos2dx V4](https://docs.cocos2d-x.org/cocos2d-x/v4/en/)

## File structure

Comparing to original project:
* [dragonBones](https://github.com/DragonBones/DragonBonesCPP/tree/master/DragonBones/src/dragonBones) moved to [Classes](https://github.com/beardog-ukr/dragonbones-cocos2dx-v4-demo/tree/master/DemoProj/Classes)
* [cocos2dx](https://github.com/DragonBones/DragonBonesCPP/tree/master/Cocos2DX_3.x/src/dragonBones/cocos2dx) folder moved to [DemoProj/Classes/dragonBones](https://github.com/beardog-ukr/dragonbones-cocos2dx-v4-demo/tree/master/DemoProj/Classes/dragonBones)
* [Demos/Classes](https://github.com/DragonBones/DragonBonesCPP/tree/master/Cocos2DX_3.x/Demos/Classes) content moved to [DemoProj/Classes](https://github.com/beardog-ukr/dragonbones-cocos2dx-v4-demo/tree/master/DemoProj/Classes)
* original [3rdParty/rapidjson](https://github.com/DragonBones/DragonBonesCPP/tree/master/3rdParty/rapidjson) moved to [DemoProj/Classes](https://github.com/beardog-ukr/dragonbones-cocos2dx-v4-demo/tree/master/DemoProj/Classes)

## Changes

Following changes were made:
* `schedule_selector` was replaced by `CC_SCHEDULE_SELECTOR` in [InverseKinematics.h](https://github.com/beardog-ukr/dragonbones-cocos2dx-v4-demo/blob/master/DemoProj/Classes/InverseKinematics.h), [CoreElement.cpp](https://github.com/beardog-ukr/dragonbones-cocos2dx-v4-demo/blob/master/DemoProj/Classes/CoreElement.cpp), and  [BoundingBox.h](https://github.com/beardog-ukr/dragonbones-cocos2dx-v4-demo/blob/master/DemoProj/Classes/BoundingBox.h)
* `Texture2D` replaced with `backend` in [CCFactory.cpp](https://github.com/beardog-ukr/dragonbones-cocos2dx-v4-demo/blob/master/DemoProj/Classes/dragonBones/cocos2dx/CCFactory.cpp)
* `{ GL_ONE, GL_ONE };` replaced by `{ cocos2d::backend::BlendFactor::ONE, cocos2d::backend::BlendFactor::ONE };` in [CCSlot.cpp](https://github.com/beardog-ukr/dragonbones-cocos2dx-v4-demo/blob/master/DemoProj/Classes/dragonBones/cocos2dx/CCSlot.cpp)
* changed arguments for `_trianglesCommand.init()` call in [CCArmatureDisplay.cpp](https://github.com/beardog-ukr/dragonbones-cocos2dx-v4-demo/blob/master/DemoProj/Classes/dragonBones/cocos2dx/CCArmatureDisplay.cpp)

