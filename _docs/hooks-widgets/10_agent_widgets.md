---
title: Change design of Agents listing
category: Hooks & Widgets
order: 10
---

If you want to change property listing, you need to open following file:

`Project_HOME  > lib > hooks_v2.dart`

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

