# Unity Project Configuration

Configure your Unity project specifically for the Moon AR platform requirements.

## Project Settings

### Player Settings

Navigate to **Edit → Project Settings → Player**:

```csharp
// Required settings for Moon AR
PlayerSettings.SetScriptingBackend(BuildTargetGroup.Android, ScriptingImplementation.IL2CPP);
PlayerSettings.Android.minSdkVersion = AndroidSdkVersions.AndroidApiLevel28;
PlayerSettings.Android.targetSdkVersion = AndroidSdkVersions.AndroidApiLevel33;
```

### Build Settings

| Setting | Value | Reason |
|---------|-------|--------|
| **Platform** | Android | Target device OS |
| **Texture Compression** | ETC2 | Hardware compatibility |
| **Scripting Backend** | IL2CPP | Performance optimization |
| **Target Architectures** | ARM64 only | Storage constraints |

## Package Management

### Essential Packages

Add to `Packages/manifest.json`:

```json
{
  "dependencies": {
    "com.unity.inputsystem": "1.5.1",
    "com.google.external-dependency-manager": "1.2.178",
    "com.unity.textmeshpro": "3.0.6"
  }
}
```

### External Dependency Manager

1. Install EDM4U via Package Manager
2. Configure for Android development:

**Create:** `Assets/Editor/DependencyConfig.cs`

```csharp
[InitializeOnLoad]
public class DependencyConfig
{
    static DependencyConfig()
    {
        EditorApplication.delayCall += () =>
        {
            GooglePlayServices.PlayServicesResolver.Resolve();
        };
    }
}
```

**Create:** `InputActions/MoonARControls.inputactions`

```json
{
  "maps": [
    {
      "name": "MoonAR",
      "actions": [
        {
          "name": "Select",
          "type": "Button",
          "bindings": {
            "path": "/space"
          }
        }
      ]
    }
  ]
}
```

## Scene Configuration

### Camera Setup

```csharp
public class MoonARCamera : MonoBehaviour
{
    void Start()
    {
        var camera = GetComponent<Camera>();
        camera.fieldOfView = 45f; // Optimized for AR glasses
        camera.nearClipPlane = 0.1f;
        camera.farClipPlane = 50f;
    }
}
```

### UI Canvas Configuration

```csharp
public class WorldSpaceUI : MonoBehaviour
{
    void Start()
    {
        var canvas = GetComponent<Canvas>();
        canvas.renderMode = RenderMode.WorldSpace;
        canvas.worldCamera = Camera.main;

        // Position at comfortable viewing distance
        transform.position = new Vector3(0, 0, 1f);
        transform.localScale = Vector3.one * 0.001f; // Scale for readability
    }
}
```

!!! tip "Performance Optimization"
    Keep total triangle count under 1.2M and maintain consistent 30 FPS on Qualcomm AR2 chips.
