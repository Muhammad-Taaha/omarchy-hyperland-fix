# 🛠️ Fix Hyprland Config Errors (Omarchy + New Hyprland)

This guide helps you fix common **Hyprland config errors** when using **Omarchy configs on newer Hyprland versions**.

---

## 🚨 Problem

After installing or updating Hyprland, you may see errors like:


invalid field type scrolltouchpad
invalid field class:* missing a value
invalid field nofocus: missing a value
config option dwindle:pseudotile does not exist


And experience:

- ❌ Keybinds not working  
- ❌ Apps not launching  
- ❌ System feels frozen/unusable  

---

## 🧠 Root Cause

Omarchy configs are written for **older Hyprland versions**.

Newer Hyprland versions have:
- Removed some options
- Changed syntax
- Dropped deprecated features

👉 Result: **Config mismatch**

---

## ✅ Solution (Step-by-Step)

---

### 1. Edit Main Config

```bash
nvim ~/.config/hypr/hyprland.conf

#2. Disable Broken Omarchy Files
Comment out these lines:

bash
# source = ~/.local/share/omarchy/default/hypr/looknfeel.conf
# source = ~/.local/share/omarchy/default/hypr/windows.conf
# source = ~/.local/share/omarchy/default/hypr/apps.conf
# source = ~/.local/share/omarchy/default/hypr/bindings/tiling.conf
3. Keep Only Safe Files
bash
source = ~/.local/share/omarchy/default/hypr/autostart.conf
source = ~/.local/share/omarchy/default/hypr/envs.conf
source = ~/.local/share/omarchy/default/hypr/input.conf
source = ~/.local/share/omarchy/default/hypr/bindings/media.conf
source = ~/.local/share/omarchy/default/hypr/bindings/utilities.conf
4. Fix scrolltouchpad Error
Open:

bash
nvim ~/.config/hypr/input.conf
❌ Remove this line:

bash
windowrule = scrolltouchpad 1.5, tag:terminal
👉 This feature was removed in newer Hyprland

5. Fix Old Input Options
Remove any of:

bash
scrolltouchpad = ...
6. Reload Hyprland
bash
hyprctl reload
