# Moon Technologies AR Platform Documentation

Welcome to the comprehensive developer documentation for the Moon Technologies AR glasses platform - a custom Android 9-based wearable device designed for immersive augmented reality experiences.

## Platform Overview

The Moon AR platform is built on:

- **Custom Android 9 ROM** optimized for AR applications
- **Qualcomm-based processor** with 4GB RAM and 4GB eMMC storage
- **Advanced sensor array** including RGB camera, dual NIR eye-tracking cameras, 6DoF IMU
- **Unity 2021.3.33 LTS** for spatial user interfaces

## Key Features

| Component | Capability | Developer Access |
|-----------|------------|------------------|
| Eye Tracking | Precise gaze cursor | System-level integration only |
| RGB Camera | Computer vision tasks | Exclusive access required |
| Gesture Input | Wristband neural sensing | Broadcast intent system |
| Touch Interface | Capacitive slider | Mapped to Unity input |

## Development Model

The platform follows a **two-phase development approach**:

1. **Android Plugin Layer**: Core functionality in Java/Kotlin
2. **Unity Presentation Layer**: 3D spatial UI and user experience

!!! warning "Camera Exclusivity"
    RGB and eye-tracking cameras cannot operate simultaneously. The SDK handles automatic switching based on application requirements.

## Quick Start

1. [Set up your development environment](getting-started/environment-setup.md)
2. [Connect to your Moon AR device](getting-started/device-connection.md)
3. [Create your first Unity project](getting-started/first-project.md)
4. [Deploy and test](getting-started/basic-testing.md)

## Support

For technical support and hardware access, please contact the Moon Technologies development team:

**📧 Email:** [admin@moontechnologies.com](mailto:admin@moontechnologies.com)

