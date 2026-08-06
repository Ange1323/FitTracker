# Release checks — version 3.0.0

Checks completed before packaging:

- inline application JavaScript passed `node --check`;
- service-worker JavaScript passed `node --check`;
- `manifest.webmanifest` parsed as valid JSON;
- HTML parsed successfully and contains no duplicate element IDs;
- every `el("...")` lookup resolves to an element ID in the application;
- legacy storage keys loaded correctly:
  - `rt_meas`
  - `rt_nutri`
  - `rt_preset`
  - `rt_adj`
  - `rt_recipes`
- Apple Health payload tests passed for:
  - the `RECOMP_HEALTH_V1` clipboard format;
  - JSON input;
  - query-string and encoded callback input;
  - decimal commas, units, spaces, and thousands separators;
  - invalid dates and out-of-range values;
- activity sync was verified to write only `rt_activity`, leaving the exact existing strings under all legacy keys unchanged;
- partial re-imports merge with an existing activity day instead of erasing omitted metrics;
- the service-worker cache is versioned as `recomp-pwa-v3-apple-health`.

## Device check still required

Health permissions and the exact Shortcuts action labels are controlled by iOS. After deployment, run the Shortcut once on the iPhone, approve Health access, and import one record in Recomp. This cannot be fully simulated outside an Apple device.
