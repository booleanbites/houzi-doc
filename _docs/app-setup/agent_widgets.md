---
title: Change design of Agents listing
category: App Setup
order: 11
---

If you want to change property listing, you need to open following file:

`Project_HOME  > lib > Hooks.dart`

Look for the `getAgentItemHook()` method. The Agent instance is provided to you, return the widget that you want to show. eg: 
```
  …
    AgentItemHook agentItemHook = (Agent agent) {
      return Container(
        child: Center(child: Text(agent.title)),
      );
    };
  …
```

