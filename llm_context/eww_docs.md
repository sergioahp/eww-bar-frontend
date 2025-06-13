# Eww (ElKowar's Wacky Widgets) Documentation

## Overview
Eww (ElKowar's Wacky Widgets) is a standalone widget system written in Rust that allows users to create custom widgets for any window manager. It's independent of window managers and provides flexible widget creation similar to AwesomeWM.

## Installation

### Prerequisites
Required system libraries:
- gtk3
- gtk-layer-shell (for Wayland)
- pango
- gdk-pixbuf2
- libdbusmenu-gtk3
- cairo
- glib2
- gcc-libs
- glibc
- Rust (recommended via rustup)

### Installation Steps
1. Clone the repository:
   ```bash
   git clone https://github.com/elkowar/eww
   ```

2. Build for X11:
   ```bash
   cargo build --release --no-default-features --features x11
   ```

3. Build for Wayland:
   ```bash
   cargo build --release --no-default-features --features=wayland
   ```

### Running Eww
1. Navigate to release directory
2. Make binary executable:
   ```bash
   chmod +x ./eww
   ```
3. Start daemon:
   ```bash
   ./eww daemon
   ```
4. Open window:
   ```bash
   ./eww open <window_name>
   ```

## Configuration

### File Structure
Eww requires two primary configuration files placed in `~/.config/eww/`:
- `eww.yuck` - Main configuration using "yuck" language (S-expressions)
- `eww.scss` or `eww.css` - Styling

### Key Configuration Components

#### 1. Windows (`defwindow`)
Define window properties including:
- Monitor selection
- Geometry (x/y coordinates, width/height)
- Positioning and anchor points

#### 2. Widgets (`defwidget`)
Create custom widgets with:
- Optional parameters
- Child widget rendering capability
- Dynamic content through variables

#### 3. Variable Types

**Basic Variables (`defvar`):**
- Manually updated variables

**Polling Variables (`defpoll`):**
- Automatically update at specified intervals

**Listening Variables (`deflisten`):**
- Update based on script output changes

**Built-in "Magic" Variables:**
- Pre-defined system information variables

### Advanced Features
- Dynamic widget generation with `literal`
- Window arguments and IDs for flexible configurations
- Generate widget lists from JSON using `for`
- Configuration file splitting via `include`

## Available Widgets

Eww provides comprehensive widgets with common properties like `class`, `valign`, `halign`, `width`, `height`, and `style`:

1. **Combo Box Text** - User selection from item lists
2. **Expander** - Show/hide child widgets
3. **Revealer** - Reveals children with animations
4. **Checkbox** - Toggleable with event handling
5. **Color Button/Chooser** - Color selection and changes
6. **Scale** - Interactive slider with value ranges
7. **Progress Bar** - Visual progress display
8. **Input** - Text entry fields
9. **Button** - Clickable with event triggers
10. **Image** - Display images with various properties
11. **Box** - Layout container
12. **Label** - Advanced text display widget
13. **Calendar** - Date selection widget
14. **Systray** - System notification icons

Each widget has unique properties tailored to its specific functionality.

## Examples and Resources

### Documentation Links
- Main documentation: https://elkowar.github.io/eww
- Beginner guide: https://dharmx.is-a.dev/eww-powermenu/

### Example Configurations
Examples are available in the `examples/` directory of the GitHub repository, including:
- Eww bar configurations
- Data structure demonstrations
- Various widget implementations

### Community Contributions
The project encourages community contributions with examples of:
- Status bars
- Dashboards
- System information displays
- Custom desktop widgets

## Key Features
- Cross-platform widget system
- Customizable theming with CSS/SCSS
- Independent of window manager
- Supports both X11 and Wayland
- Flexible S-expression based configuration
- Dynamic content updating