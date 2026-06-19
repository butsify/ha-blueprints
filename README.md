# Home Assistant Blueprints

Simple Home Assistant automation blueprints for practical use cases.

## Included Blueprint

- `Linked Analog Entities (Simple)`
  - File: `blueprints/automation/ha-blueprints/linked-analog-entities.yaml`
  - Links two selected entities and mirrors numeric values both directions.
  - Supported selectable domains: `sensor`, `number`, `input_number`.
  - Writable targets: `number`, `input_number`.
  - Optional auto-clamp to target min/max to avoid out_of_range errors.
  - No debounce logic.

## Important Behavior

- If one side is a `sensor`, it is treated as a source (read-only).
- The automation writes only to writable entities.
- `unknown` and `unavailable` values are ignored automatically because non-numeric states are not written.
- If both selected entities are `sensor`, no write is possible and sync will not occur.

## Install In Home Assistant

1. Open Home Assistant.
2. Go to Settings -> Automations & Scenes -> Blueprints.
3. Import blueprint from URL.
4. Use this raw URL:

  `https://raw.githubusercontent.com/butsify/ha-blueprints/main/blueprints/automation/ha-blueprints/linked-analog-entities.yaml`

## Create An Automation From The Blueprint

1. Create automation from `Linked Analog Entities (Simple)`.
2. Select `Entity A` and `Entity B`.
3. Set `Tolerance` (default `0`).
4. Keep `Clamp To Target Range` enabled (recommended).
5. Save and test by changing values on either side.

## Notes

- For best bidirectional behavior, use `number`/`input_number` on both sides.
- If one side is `sensor`, sync can only flow toward the writable side.

## Troubleshooting

- If you see `out_of_range` in automation traces, your target `number`/`input_number` limits are lower than the source value.
- Re-import/update the blueprint in Home Assistant and re-save automations created from it so new logic is applied.
