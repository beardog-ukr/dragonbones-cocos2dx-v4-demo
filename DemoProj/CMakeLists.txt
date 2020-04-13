cmake_minimum_required(VERSION 3.6)

set(APP_NAME DragonBonesDemo)

project(${APP_NAME})

if(XCODE)
    if(NOT DEFINED CMAKE_XCODE_ATTRIBUTE_IPHONEOS_DEPLOYMENT_TARGET)
        SET (CMAKE_XCODE_ATTRIBUTE_IPHONEOS_DEPLOYMENT_TARGET 8.0)
    endif()
endif()

if(NOT DEFINED BUILD_ENGINE_DONE) # to test LimeChihuahua into root project
    set(COCOS2DX_ROOT_PATH ${CMAKE_CURRENT_SOURCE_DIR}/cocos2d)
    set(CMAKE_MODULE_PATH ${COCOS2DX_ROOT_PATH}/cmake/Modules/)

    include(CocosBuildSet)
    add_subdirectory(${COCOS2DX_ROOT_PATH}/cocos ${ENGINE_BINARY_PATH}/cocos/core)
endif()

# record sources, headers, resources...
set(GAME_SOURCE)
set(GAME_HEADER)

set(GAME_RES_FOLDER
    "${CMAKE_CURRENT_SOURCE_DIR}/Resources"
    )
if(APPLE OR WINDOWS)
    cocos_mark_multi_resources(common_res_files RES_TO "Resources" FOLDERS ${GAME_RES_FOLDER})
endif()

# add cross-platforms source files and header files 
list(APPEND GAME_SOURCE
     Classes/AppDelegate.cpp
Classes/CoreElement.cpp
Classes/DragHelper.cpp
Classes/dragonBones/geom/Transform.cpp
Classes/dragonBones/geom/Point.cpp
Classes/dragonBones/animation/TimelineState.cpp
Classes/dragonBones/animation/Animation.cpp
Classes/dragonBones/animation/WorldClock.cpp
Classes/dragonBones/animation/AnimationState.cpp
Classes/dragonBones/animation/BaseTimelineState.cpp
Classes/dragonBones/model/CanvasData.cpp
Classes/dragonBones/model/ArmatureData.cpp
Classes/dragonBones/model/UserData.cpp
Classes/dragonBones/model/AnimationConfig.cpp
Classes/dragonBones/model/ConstraintData.cpp
Classes/dragonBones/model/DisplayData.cpp
Classes/dragonBones/model/SkinData.cpp
Classes/dragonBones/model/TextureAtlasData.cpp
Classes/dragonBones/model/AnimationData.cpp
Classes/dragonBones/model/DragonBonesData.cpp
Classes/dragonBones/model/BoundingBoxData.cpp
Classes/dragonBones/event/EventObject.cpp
Classes/dragonBones/armature/Slot.cpp
Classes/dragonBones/armature/DeformVertices.cpp
Classes/dragonBones/armature/Armature.cpp
Classes/dragonBones/armature/Bone.cpp
Classes/dragonBones/armature/TransformObject.cpp
Classes/dragonBones/armature/Constraint.cpp
Classes/dragonBones/core/BaseObject.cpp
Classes/dragonBones/core/DragonBones.cpp
Classes/dragonBones/parser/JSONDataParser.cpp
Classes/dragonBones/parser/BinaryDataParser.cpp
Classes/dragonBones/parser/DataParser.cpp
Classes/dragonBones/factory/BaseFactory.cpp
Classes/dragonBones/cocos2dx/CCSlot.cpp
Classes/dragonBones/cocos2dx/CCArmatureDisplay.cpp
Classes/dragonBones/cocos2dx/CCTextureAtlasData.cpp
Classes/dragonBones/cocos2dx/CCFactory.cpp
     )
list(APPEND GAME_HEADER
     Classes/AppDelegate.h
Classes/AnimationBase.h
Classes/AnimationLayer.h
Classes/BaseDemo.h
Classes/BoneOffset.h
Classes/CoreElement.h
Classes/DragHelper.h
Classes/DragonBonesEvent.h
Classes/HelloDragonBones.h
Classes/InverseKinematics.h
Classes/PerformanceTest.h
Classes/ReplaceAnimation.h
Classes/ReplaceSlotDisplay.h
Classes/ReplaceSkin.h
Classes/rapidjson/rapidjson.h
Classes/rapidjson/encodings.h
Classes/rapidjson/memorystream.h
Classes/rapidjson/stream.h
Classes/rapidjson/internal/pow10.h
Classes/rapidjson/internal/ieee754.h
Classes/rapidjson/internal/strtod.h
Classes/rapidjson/internal/swap.h
Classes/rapidjson/internal/meta.h
Classes/rapidjson/internal/strfunc.h
Classes/rapidjson/internal/stack.h
Classes/rapidjson/internal/diyfp.h
Classes/rapidjson/internal/itoa.h
Classes/rapidjson/internal/biginteger.h
Classes/rapidjson/internal/dtoa.h
Classes/rapidjson/internal/regex.h
Classes/rapidjson/schema.h
Classes/rapidjson/pointer.h
Classes/rapidjson/encodedstream.h
Classes/rapidjson/error/error.h
Classes/rapidjson/error/en.h
Classes/rapidjson/allocators.h
Classes/rapidjson/istreamwrapper.h
Classes/rapidjson/msinttypes/inttypes.h
Classes/rapidjson/msinttypes/stdint.h
Classes/rapidjson/fwd.h
Classes/rapidjson/filewritestream.h
Classes/rapidjson/ostreamwrapper.h
Classes/rapidjson/filereadstream.h
Classes/rapidjson/memorybuffer.h
Classes/rapidjson/prettywriter.h
Classes/rapidjson/writer.h
Classes/rapidjson/reader.h
Classes/rapidjson/stringbuffer.h
Classes/rapidjson/document.h
Classes/dragonBones/geom/Rectangle.h
Classes/dragonBones/geom/Transform.h
Classes/dragonBones/geom/Point.h
Classes/dragonBones/geom/ColorTransform.h
Classes/dragonBones/geom/Matrix.h
Classes/dragonBones/animation/AnimationState.h
Classes/dragonBones/animation/Animation.h
Classes/dragonBones/animation/IAnimatable.h
Classes/dragonBones/animation/WorldClock.h
Classes/dragonBones/animation/TimelineState.h
Classes/dragonBones/animation/BaseTimelineState.h
Classes/dragonBones/model/BoundingBoxData.h
Classes/dragonBones/model/TextureAtlasData.h
Classes/dragonBones/model/UserData.h
Classes/dragonBones/model/AnimationData.h
Classes/dragonBones/model/SkinData.h
Classes/dragonBones/model/CanvasData.h
Classes/dragonBones/model/DisplayData.h
Classes/dragonBones/model/DragonBonesData.h
Classes/dragonBones/model/AnimationConfig.h
Classes/dragonBones/model/ArmatureData.h
Classes/dragonBones/model/ConstraintData.h
Classes/dragonBones/event/IEventDispatcher.h
Classes/dragonBones/event/EventObject.h
Classes/dragonBones/armature/Bone.h
Classes/dragonBones/armature/Armature.h
Classes/dragonBones/armature/IArmatureProxy.h
Classes/dragonBones/armature/DeformVertices.h
Classes/dragonBones/armature/TransformObject.h
Classes/dragonBones/armature/Slot.h
Classes/dragonBones/armature/Constraint.h
Classes/dragonBones/DragonBonesHeaders.h
Classes/dragonBones/core/DragonBones.h
Classes/dragonBones/core/BaseObject.h
Classes/dragonBones/parser/DataParser.h
Classes/dragonBones/parser/BinaryDataParser.h
Classes/dragonBones/parser/JSONDataParser.h
Classes/dragonBones/factory/BaseFactory.h
Classes/dragonBones/cocos2dx/CCDragonBonesHeaders.h
Classes/dragonBones/cocos2dx/CCFactory.h
Classes/dragonBones/cocos2dx/CCArmatureDisplay.h
Classes/dragonBones/cocos2dx/CCTextureAtlasData.h
Classes/dragonBones/cocos2dx/CCSlot.h
     )

if(ANDROID)
    # change APP_NAME to the share library name for Android, it's value depend on AndroidManifest.xml
    set(APP_NAME MyGame)
    list(APPEND GAME_SOURCE
         proj.android/app/jni/hellocpp/main.cpp
         )
elseif(LINUX)
    list(APPEND GAME_SOURCE
         proj.linux/main.cpp
         )
elseif(WINDOWS)
    list(APPEND GAME_HEADER
         proj.win32/main.h
         proj.win32/resource.h
         )
    list(APPEND GAME_SOURCE
         proj.win32/main.cpp
         proj.win32/game.rc
         ${common_res_files}
         )
elseif(APPLE)
    if(IOS)
        list(APPEND GAME_HEADER
             proj.ios_mac/ios/AppController.h
             proj.ios_mac/ios/RootViewController.h
             )
        set(APP_UI_RES
            proj.ios_mac/ios/LaunchScreen.storyboard
            proj.ios_mac/ios/LaunchScreenBackground.png
            proj.ios_mac/ios/Images.xcassets
            )
        list(APPEND GAME_SOURCE
             proj.ios_mac/ios/main.m
             proj.ios_mac/ios/AppController.mm
             proj.ios_mac/ios/RootViewController.mm
             proj.ios_mac/ios/Prefix.pch
             ${APP_UI_RES}
             )
    elseif(MACOSX)
        set(APP_UI_RES
            proj.ios_mac/mac/Icon.icns
            proj.ios_mac/mac/Info.plist
            )
        list(APPEND GAME_SOURCE
             proj.ios_mac/mac/main.cpp
             proj.ios_mac/mac/Prefix.pch
             ${APP_UI_RES}
             )
    endif()
    list(APPEND GAME_SOURCE ${common_res_files})
endif()

# mark app complie info and libs info
set(all_code_files
    ${GAME_HEADER}
    ${GAME_SOURCE}
    )
if(NOT ANDROID)
    add_executable(${APP_NAME} ${all_code_files})
else()
    add_library(${APP_NAME} SHARED ${all_code_files})
    add_subdirectory(${COCOS2DX_ROOT_PATH}/cocos/platform/android ${ENGINE_BINARY_PATH}/cocos/platform)
    target_link_libraries(${APP_NAME} -Wl,--whole-archive cpp_android_spec -Wl,--no-whole-archive)
endif()

target_link_libraries(${APP_NAME} cocos2d)
target_include_directories(${APP_NAME}
        PRIVATE Classes
        PRIVATE ${COCOS2DX_ROOT_PATH}/cocos/audio/include/
)

# mark app resources
setup_cocos_app_config(${APP_NAME})
if(APPLE)
    set_target_properties(${APP_NAME} PROPERTIES RESOURCE "${APP_UI_RES}")

    if(MACOSX)
        set_xcode_property(${APP_NAME} INFOPLIST_FILE "${CMAKE_CURRENT_SOURCE_DIR}/proj.ios_mac/mac/Info.plist")
    elseif(IOS)
        set_xcode_property(${APP_NAME} INFOPLIST_FILE "${CMAKE_CURRENT_SOURCE_DIR}/proj.ios_mac/ios/Info.plist")
        set_xcode_property(${APP_NAME} ASSETCATALOG_COMPILER_APPICON_NAME "AppIcon")
    endif()

    # For code-signing, set the DEVELOPMENT_TEAM:
    #set_xcode_property(${APP_NAME} DEVELOPMENT_TEAM "GRLXXXX2K9")
elseif(WINDOWS)
    cocos_copy_target_dll(${APP_NAME})
endif()

if(LINUX OR WINDOWS)
    cocos_get_resource_path(APP_RES_DIR ${APP_NAME})
    cocos_copy_target_res(${APP_NAME} LINK_TO ${APP_RES_DIR} FOLDERS ${GAME_RES_FOLDER})
endif()
