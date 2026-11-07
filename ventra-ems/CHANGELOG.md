# Ventra-EMS release notes

## Next release

### Changed
- **Adding devices.** Open the Home circle and choose "Add device": one list of every device type, each with a short explanation. The "+" circles are gone from the overview, and the Home window now has its own Edit button.
- **Jump to the device in Home Assistant.** Each device window has buttons that open the Home Assistant page of the devices behind it.
- **Draw the lines yourself (free layout).** Tap a line in edit mode: it comes to the front, and you can drag every piece of it and every corner, and remove a bend.
- **Every battery in the charge level graph.** The All batteries window shows each battery's charge level next to the average.
- **Arrange the basic view.** Edit mode now keeps the basic view, so you can drag its circles and use the free layout there too.

### Fixed
- **Keep on when full with planned charging.** When planned charging reaches its target charge level, the car now counts as full, so the charger stays on and the car can preheat from it.
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
