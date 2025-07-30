# Development Environment Setup

This guide walks you through setting up your development environment for Moon AR application development.

## Unity Development Environment

### Install Unity 2021.3.33 LTS

1. Download Unity Hub from the official Unity website
2. Install Unity 2021.3.33f1 LTS through Unity Hub
3. Include Android Build Support module during installation

### Required Unity Packages

Add these packages via Window → Package Manager:

```json
{
  "dependencies": {
    "com.unity.inputsystem": "1.5.1",
    "com.google.external-dependency-manager": "1.2.178"
  }
}
```

!!! note "No AR Foundation Required"
    The Moon AR platform uses a custom ROM that handles AR functionality. Do not install AR Foundation or XR packages.

## Android Development Environment

### Install Android Studio

1. Download Android Studio (Hedgehog or later)
2. Install SDK platforms for API levels 28-33
3. Configure Android SDK build tools

### SDK Configuration

Verify SDK installation:

```bash
android list targets
```

Install required platforms:

```bash
sdkmanager "platforms;android-28"
sdkmanager "platforms;android-33"
sdkmanager "build-tools;33.0.0"
```

## Development Machine Requirements

| Component | Minimum | Recommended |
|-----------|---------|-------------|
| OS | Windows 10, macOS 10.15, Ubuntu 18.04 | Latest versions |
| RAM | 8GB | 16GB+ |
| Storage | 50GB free | 100GB+ |
| Graphics | DirectX 9.0c compatible | Dedicated GPU |

## Verification

Test your setup:

Check Unity installation:

```bash
unity -version
```

Verify Android tools:

```bash
adb version
```

Your environment is ready when both commands return version information without errors.

