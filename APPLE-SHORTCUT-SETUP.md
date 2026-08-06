# Build the “Recomp Health Sync” Shortcut

The web app cannot read HealthKit directly. This Shortcut reads the current day from Apple Health, creates one text record, copies it to the clipboard, and finishes. Recomp then imports that record into the separate `rt_activity` store.

The exact label of an action can vary slightly by iOS version or language. Search the Shortcuts action list using the bold action names below.

## 1. Create the Shortcut

1. Open **Shortcuts** on the iPhone.
2. Tap **+** to create a new shortcut.
3. Name it exactly:

   `Recomp Health Sync`

The Recomp button launches a Shortcut with this exact name.

## 2. Create today’s date value

1. Add **Current Date**.
2. Add **Format Date**.
3. Set the date format to **Custom**.
4. Enter this format:

   `yyyy-MM-dd`

5. Rename the formatted result variable to `SyncDate` if you find this helpful.

## 3. Read Active Energy

1. Add **Find Health Samples**.
2. Configure its filters:
   - Type: **Active Energy**
   - Start Date: **is today**
   - Source: your **Apple Watch**, when the Source filter is available
3. Add **Get Details of Health Samples** and choose **Value**. If your version lets **Calculate Statistics** accept the samples directly, this intermediate action can be omitted.
4. Add **Calculate Statistics** and choose **Sum**.
5. Rename the result `Active`.

## 4. Read Resting Energy

Repeat the same pattern:

- Type: **Resting Energy** or **Basal Energy Burned**
- Start Date: **is today**
- Source: your Apple Watch, when available
- Details: **Value**
- Statistics: **Sum**
- Result name: `Resting`

## 5. Read Steps

Repeat the pattern:

- Type: **Steps** or **Step Count**
- Start Date: **is today**
- Source: your Apple Watch, when available
- Details: **Value**
- Statistics: **Sum**
- Result name: `Steps`

## 6. Read Exercise Minutes

Repeat the pattern:

- Type: **Apple Exercise Time** or **Exercise Minutes**
- Start Date: **is today**
- Source: your Apple Watch, when available
- Details: **Value**
- Statistics: **Sum**
- Result name: `Exercise`

If your iPhone does not expose an exercise-time sample in Shortcuts, omit this value. Recomp accepts a record containing only the other fields.

## 7. Build the Recomp record

Add a **Text** action. Enter the line below, replacing each bracketed placeholder with its Magic Variable:

`RECOMP_HEALTH_V1|date=[SyncDate]|active=[Active]|resting=[Resting]|steps=[Steps]|exercise=[Exercise]`

The app accepts values containing units, spaces, decimal commas, or thousands separators. Do not change the field names before the equals signs.

## 8. Copy and finish

1. Add **Copy to Clipboard**, using the Text result.
2. Optionally add **Show Notification** with:

   `Recomp Health data copied`

3. Run the Shortcut once inside Shortcuts. Approve the requested Health permissions.

## 9. Use it from Recomp

1. Open the Recomp Home Screen app.
2. Tap **Sync Apple Health**.
3. Shortcuts runs. It normally returns to Recomp; if iOS leaves you in Shortcuts, switch back to the Recomp Home Screen app.
4. Tap **Import copied data**.
5. Approve the clipboard paste prompt if iOS shows one.

The record overwrites only the same date in `rt_activity`. It does not change nutrition, measurements, recipes, presets, or calorie targets.

## Troubleshooting

- **Shortcut not found:** verify the exact name `Recomp Health Sync`.
- **Clipboard is empty:** run the Shortcut directly and confirm the last data action is **Copy to Clipboard**.
- **No recognised values:** verify the Text action starts with `RECOMP_HEALTH_V1|` and uses the field names shown above.
- **A value is unexpectedly high:** add the Source filter for your Apple Watch so iPhone and Watch samples are not both summed.
- **Exercise is unavailable:** remove `|exercise=[Exercise]`; the other fields still import.
- **Test without the Shortcut:** open the side menu, expand **Shortcut setup & manual fallback**, and enter the values manually.
