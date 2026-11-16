# Ventra-EMS release notes

## Next release

### New
- **A meter for a battery.** A battery window can now have its own power meter (optional), shown in its window and under its circle, like the meter of an inverter or EV charger. Ventra-EMS doesn't steer on it.
- **One plan for buying and selling.** Every 15 minutes Ventra-EMS plans the coming 24 hours: with all known prices (and the usual prices after them), the expected use of the house and the cars, and the expected solar, corrected by how far off the forecast was the past days. It compares every way to run the batteries and picks the cheapest: cover the house, buy cheap energy for when it is needed, hold the energy for the expensive hours, or sell when that earns more than keeping it. Solar always comes first, and it only buys, sells or holds when that saves at least €0.02 per kWh. Planned EV charging ("ready by") takes its moments from the same plan. It plans again at once when a setting, the prices, the forecast or a car changes, or when the batteries are off the plan. Buying and selling are each Automatic or Off; every installation starts on Automatic. The old buy and sell choices (above or below a price, the most expensive or cheapest hours, every day, a fixed amount) and their settings are gone; "Stop buying at" is now "Charge from the grid at most to" and "Stop selling at" is "Sell down to". The Planner window has a Tuning section (how far ahead, how fast it learns, the solar and the unknown prices it plans with); the defaults suit most homes.
- **A planner circle and a Planner window.** Above the grid circle, the planner circle shows what the plan does now (buy, hold, zero or sell), its next step (e.g. "Sell at 18:00") and the coming 12 hours as a coloured bar. It takes the place of the buy and sell card. Click it to open the Planner window: the reason now, what the plan costs, a graph of the coming hours and of the past 12 hours (what happened against what was planned), the planned buying and selling periods with kWh and euros, the plan per hour, and all buying, selling and planner settings, moved here from the Grid window.
- **Batteries are charged back below their lowest charge level.** Some inverters slowly drain their battery even when they should do nothing; when the battery gets more than 2 % below its lowest level, Ventra-EMS charges it back (0.5 kW, solar first). On for every battery, with its own settings.
- **Buy power and sell power.** In the Grid window, under buying and selling, you set how fast the batteries buy from and sell to the grid, together; solar comes on top. Both start at 10 kW, also on an existing installation: raise them if your batteries bought or sold faster before.

### Changed
- **A new mode: hold.** While the plan holds the batteries, the mode shows "Auto-Hold": the house uses the grid now, and the batteries keep their energy for a more expensive moment. Solar still charges them.
- **Better starting values for a new installation or a new device.** Grid connection 17 kW with at most 16 kW import and export; batteries 5 kW with a lowest power of 0.01 kW and manual rates of 2 kW; EV chargers 4–11 kW with phase detection and "Keep on when full" on; 5 seconds to take over and hand back control; buy and sell prices that fit a market or a contract price; new OCPP glue automations round the current to 2 A. Devices and automations you already have keep their settings.
- **Live values while you choose entities.** The values under the entities in a device window now update every 5 seconds, and clicking an entity box lets you type to search right away.
- **Adding devices.** Open the Home circle and choose "Add device": one list of every device type, each with a short explanation. The "+" circles are gone from the overview, and the Home window now has its own Edit button.
- **Jump to the device in Home Assistant.** Each device window has buttons that open the Home Assistant page of the devices behind it.
- **Choose where a forced charge gets its energy.** With Force on, an EV charger now also lets you choose: solar and grid (the home battery stays for the house), solar, battery and grid, or the cheapest at that moment.
- **Place the savings line yourself (free layout).** The line with today's savings is a block on the grid that you can drag in edit mode.
- **Solar forecast in the solar window.** The solar forecast graph moved from the grid window to the solar window (All solar, or your inverter).
- **Draw the lines yourself (free layout).** Tap a line in edit mode: it comes to the front, and you can drag every piece of it and every corner, and remove a bend.
- **Every battery in the charge level graph.** The All batteries window shows each battery's charge level next to the average.
- **Arrange the basic view.** Edit mode now keeps the basic view, so you can drag its circles and use the free layout there too.
- **Same order in the grid window.** With two power meters, the import meter now comes first and the export meter second, like the meter readings below.
- **A flipped sign or a changed scale stands out.** When you flip the sign of an entity, the "Flip sign" button turns orange; a scale other than 1× turns orange too, so you see at a glance what is changed.

### Fixed
- **The plan follows a saved change at once.** After saving a setting (buy power, Charge from the grid at most to, a battery limit, an EV ready-by time …) the plan is made again straight away and the plan card updates by itself; it also refreshes while it is open.
- **The plan uses the buy power.** The plan showed the batteries buying faster than the buy power you set (up to what the grid allows); now it plans with it, as the batteries really buy. Its saving also counts the energy left in the batteries.
- **Settings only change in edit mode.** "Counts up", the scale and "Flip sign" under an entity, and the glue automation, could be changed while only viewing a window; now they need Edit, like every other setting.
- **Rule timers read "3 min of 5 min" again.** A condition that must hold for a while showed its count as "3.0 min of 5.0 min".
- **Every info mark shows its explanation.** In many places (entity fields, rules, glue automations, battery limits) the ⓘ showed nothing; now its text appears on top of the window on hover or tap, on a phone too.
- **"Counts up" starts at 0.** Ticking "Counts up" on a meter that shows its total (e.g. 500 kWh) now shows 0 kWh and from then on only what is added; it starts again at midnight and when you choose another entity. The window shows both the meter's total and what Ventra-EMS reads.
- **Emptying an entity field.** An optional entity field now has a × next to the chosen entity (or press Delete on it) to remove it; before, it was only possible from the bottom of the opened list.
- **Buying a fixed amount per day.** With "all known prices", the amount still to buy today was postponed to tomorrow's cheaper hours and then never bought; now each day's amount is bought within that day.
- **Saving in the Home window.** In edit mode the Home window now has Cancel and Save, like every other window, so its own settings can be saved.
- **Glue automations are always recognised.** A device window now always shows its glue automation, also when the online catalogue no longer offers that glueprint for your version; it keeps working as it is.
- **Batteries share a small load again.** With several batteries, a small charge or discharge could give every battery 0 because of their minimum powers; now the batteries that can run at that power take it.
- **Keep on when full with planned charging.** When planned charging reaches its target charge level, the car now counts as full, so the charger stays on and the car can preheat from it.
- **The overview keeps still.** The lines and circles no longer jump now and then, circles and their icons no longer shift a pixel when a value under them changes, and the main circles no longer move when a line of text under them appears or disappears.
- **Hover on every graph.** The values under the pointer now show in every window (the box was hidden behind the window), graphs no longer lose their hover after a few minutes, and the stacked bars in the battery and solar windows show their values too.

## 1.0.666

### New
- **Set up everything in the overview.** Add, edit and remove devices, rules and prices from the overview itself; every setting has a short explanation (ⓘ). Changes apply without a restart.
- **Free layout.** Place every circle anywhere on a grid and steer the energy lines with a handle; "Reset layout" brings back the normal arrangement.
- **Graphs in every window.** Power over the last 24 hours or 7 days, costs and earnings in euros, the battery's charge level, and the setpoint next to what a device actually does. Hover or tap for the values.
- **Costs and earnings per device.** See what the solar was worth, what the battery saved and cost, and what each device or the car cost — split over solar, battery and grid.
- **Separate buy and sell price** with your own surcharges (supplier markup, energy tax, VAT), a second market price source with automatic fallback, and a name per price source.
- **New battery strategies.** Buy and sell every day at the best moments, buy a fixed amount (or your predicted daily use) at the cheapest moments and see how much is still to buy, and block all export at low prices.
- **Maximum import for the whole home.** When the connection gets too full, Ventra-EMS uses the battery, lowers devices and switches devices off, in the order you choose.
- **EV charging.** Charge by rules per group (solar surplus, fixed power, maximum, by price, or ready by a set time at the cheapest moments), in up to 3 uninterrupted blocks, choose where the energy comes from, detect 1- or 3-phase charging, and keep the charger on when the car is full so it can preheat.
- **Rules.** Up to 3 groups with 9 conditions each, a weekly schedule, extra sensors of your own, and a condition can be required to hold for a number of minutes first.
- **Smooth handover.** Taking and releasing control of a battery, grid controller or EV charger now ramps over a short time instead of jumping.
- **Meters.** Read the smart meter's counters per tariff, and add kWh readings to a device's meter; the battery window shows its energy in and out, its round-trip efficiency and its real capacity.
- **Ready-made automations.** The device window offers the matching automation for your brand (battery, inverter, EV charger, relays), installs it and keeps it up to date.
- **Test control.** Run one battery or EV charger at a set power for a while, to check the installation.
- **Easier to read.** A modern look, basic and advanced view, power in W or kW, Dutch and English following your Home Assistant language, and a "!" at the home circle when a battery doesn't follow its setpoint.

### Changed
- The companion integration finds the add-on by itself; no address or open port is needed.
- Each device window explains what Ventra-EMS does with the device and why.
- The settings, dashboard and debug pages are combined into the overview.

### Fixed
- Many fixes in planning, price handling and device control.
