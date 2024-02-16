---
title: Agent Profile Configurations
category: Hooks & Widgets
permalink: hooks-widgets/agent_profile_configurations
order: 333
---

If you want to customize the Agent Profile such as show/hide fields like tax number, license etc, you need to open following file:

`Project_HOME  > lib > hooks_v2.dart`

Look for the `getAgentProfileConfigurationsHook()` method. Perform customization according to your requirement.

After modifications, restart the app and the changes will reflect on Maps.

```dart
@override
  AgentProfileConfigurationsHook getAgentProfileConfigurationsHook() {
    AgentProfileConfigurationsHook agentProfileConfigurationsHook = (hook) {
      if (hook == "additional_info") {
        return null;  // return true if you want to hide the whole additional information section.
      } else if (hook == "license") {
        return null;  // return true if you want to hide the license section.
      } else if (hook == "tax_number") {
        return null;  // return true if you want to hide the tax number section.
      } else if (hook == "service_areas") {
        return null;  // return true if you want to hide the service areas section.
      } else if (hook == "specialities") {
        return null;  // return true if you want to hide the specialities section.
      }

      return null;
    };
    return agentProfileConfigurationsHook;
  }
```

*Added in version 1.3.9*

