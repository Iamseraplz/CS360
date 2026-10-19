# Inventory App
**Sarah See | CS 360 Mobile Architecture and Programming**

## App Requirements and Goals

I developed an Android inventory app using Java and SQLite. The goal was to help warehouse employees and inventory managers keep track of items, update quantities, and notice when something runs out. Users can create an account, sign in, add and remove items, search inventory, and change stock quantities. The app saves accounts and inventory so that information is still available after closing it.

The app also includes optional SMS alerts when an item’s quantity drops to zero. Users can continue managing inventory and seeing in-app warnings if they deny SMS permission or turn alerts off.

## Screens and User Needs

The app includes screens for login and account creation, the inventory grid, adding items, viewing item details, changing quantities, and managing SMS settings.

I wanted common tasks to be easy to find without making users go through unnecessary steps. Item names and quantities are clearly labeled, and the inventory can be searched by name or location. The app uses the words “Out of stock” instead of relying only on color. It also asks for confirmation before deleting an item.

I kept the colors, labels, and buttons consistent across screens. Checking the layouts in Android Studio helped me catch problems like the Delete buttons getting cut off. These choices made the screens easier to follow, and testing the navigation helped me check that users could move between tasks or cancel an action.

## Development Approach

Taking the app one piece at a time worked best for me. I started with the screen layouts and navigation, then connected account creation, login, inventory storage, and quantity changes. After that, I connected the SMS settings and alert trigger.

I separated database operations, password hashing, quantity rules, and SMS handling into their own Java classes. This helped keep those responsibilities organized. Passwords are stored as salted hashes rather than readable text, and database and password operations run in the background so they do not block the screen.

I would use this approach again because smaller steps make it easier to understand what changed and find the cause of a problem.

## Testing and What I Learned

I tested the app in the Android Emulator as I added features. I checked account creation, incorrect passwords, duplicate usernames, adding items, searching, deleting, and changing quantities. I also closed and reopened the app to check that information stayed saved.

For quantity changes, I tested adding stock, subtracting stock, reaching zero, and trying to subtract more than was available. I checked that canceling an action left the information unchanged. For SMS, I tested granting permission and turning alerts off. The emulator showed that an SMS request was submitted when stock reached zero, but that did not confirm delivery to a real phone.

Testing helped me check more than whether the app worked with correct input. It also showed why users need clear feedback when something cannot be completed.

## Challenges and Solutions

One challenge was making the stock update and SMS alert work together without making inventory depend on SMS. I handled this by saving the quantity change first and then checking whether the item had gone from a positive quantity to zero. The app checks the alert setting and permission before requesting a text.

This means a denied permission or SMS problem does not undo a saved inventory change. Users still see the out-of-stock label and an in-app warning. Working through this helped me think about how features should behave when only part of an action succeeds.

## What I Am Most Proud Of

The quantity-change feature is the part I am most proud of. It previews the new total, prevents stock from going below zero, saves the change, and updates the item details and inventory grid. It also connects to the out-of-stock warning.

Seeing those parts work together made the app feel like something I could actually use. It brought together the layout, input validation, database operations, and user feedback.

## Future Plans

I want to keep expanding this app for my own use before considering a public release. My next goals are adding photos of stock and a way to back up and restore inventory. Photos would make similar items easier to identify, and backups would help protect the information if I changed or lost my phone.

The current app stores inventory locally and does not synchronize it across devices. As I add features, I want to keep testing one change at a time and make sure updates preserve existing inventory.
