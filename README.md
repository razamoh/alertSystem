# PosAlert Plugin Documentation

PosAlert is a versatile and customizable alert system designed specifically for Point of Sale (POS) applications. It provides a clean, modern UI for alerts, confirmations, prompts, and toast notifications.

## Table of Contents

- [Installation](#installation)
- [Basic Usage](#basic-usage)
- [Configuration Options](#configuration-options)
- [Alert Methods](#alert-methods)
- [Theming](#theming)
- [Toast Notifications](#toast-notifications)
- [API Reference](#api-reference)

## Installation

1. Include jQuery in your project (required dependency)
2. Download and include the PosAlert plugin script

```html
<!-- Include jQuery -->
<script src="https://code.jquery.com/jquery-3.6.0.min.js"></script>

<!-- Include PosAlert -->
<script src="path/to/jquery.posalert.js"></script>
```

## Basic Usage

Initialize the plugin:

```javascript
// Initialize with default options
$.posAlert();

// Or initialize with custom options
$.posAlert({
    theme: {
        primaryColor: '#3f51b5',
        secondaryColor: '#2196f3'
    },
    toastTimeout: 5000,
    toastPosition: 'top-right'
});
```

## Configuration Options

The plugin accepts the following configuration options:

| Option | Type | Default | Description |
|--------|------|---------|-------------|
| `theme` | Object | See below | Theme customization options |
| `toastTimeout` | Number | 3000 | Default duration for toast notifications (ms) |
| `toastPosition` | String | 'bottom-right' | Position for toast notifications |
| `zIndex` | Number | 10000 | Z-index for the alerts and toasts |

### Default Theme

```javascript
{
    primaryColor: '#2c3e50',
    secondaryColor: '#3498db',
    dangerColor: '#e74c3c',
    successColor: '#2ecc71',
    warningColor: '#f39c12',
    infoColor: '#1abc9c',
    textColor: '#333',
    backgroundColor: '#fff',
    backdropColor: 'rgba(0, 0, 0, 0.5)',
    borderRadius: '8px',
    boxShadow: '0 4px 8px rgba(0, 0, 0, 0.1)',
    fontFamily: 'Arial, sans-serif'
}
```

## Alert Methods

### Alert Dialog

```javascript
$.posAlert().alert({
    title: 'Information',
    message: 'Your transaction has been processed.',
    buttonText: 'OK',
    theme: 'primary', // primary, secondary, success, danger, warning, info
    callback: function() {
        console.log('Alert closed');
    }
});
```

### Confirm Dialog

```javascript
$.posAlert().confirm({
    title: 'Confirm Action',
    message: 'Are you sure you want to void this transaction?',
    confirmText: 'Yes, Void It',
    cancelText: 'Cancel',
    theme: 'danger',
    onConfirm: function() {
        console.log('Action confirmed');
    },
    onCancel: function() {
        console.log('Action cancelled');
    }
});
```

### Prompt Dialog

```javascript
$.posAlert().prompt({
    title: 'Discount',
    message: 'Enter discount amount:',
    placeholder: '0.00',
    defaultValue: '',
    theme: 'primary',
    onConfirm: function(value) {
        console.log('Entered value:', value);
    }
});
```

## Theming

You can update the theme at runtime:

```javascript
$.posAlert().updateTheme({
    primaryColor: '#673ab7',
    secondaryColor: '#2196f3',
    borderRadius: '4px'
});
```

## Toast Notifications

### Display Toasts

```javascript
// Success toast
$.posAlert().toast({
    message: 'Item added to cart successfully!',
    type: 'success',
    duration: 3000
});

// Error toast
$.posAlert().toast({
    message: 'Error: Could not connect to payment terminal.',
    type: 'error',
    duration: 5000
});

// Warning toast
$.posAlert().toast({
    message: 'Printer paper is low.',
    type: 'warning'
});

// Info toast
$.posAlert().toast({
    message: 'New update available.',
    type: 'info'
});
```

### Toast Position

Change the position of toast notifications:

```javascript
$.posAlert().setToastPosition('top-right'); // 'top-right', 'top-left', 'bottom-right', 'bottom-left'
```

### Toast Duration

Set the default duration for toast notifications:

```javascript
$.posAlert().setToastTimeout(4000); // milliseconds
```

## API Reference

| Method | Description |
|--------|-------------|
| `alert(options)` | Display an alert dialog |
| `confirm(options)` | Display a confirmation dialog |
| `prompt(options)` | Display a prompt dialog |
| `toast(options)` | Display a toast notification |
| `updateTheme(options)` | Update theme settings |
| `setToastPosition(position)` | Set toast notification position |
| `setToastTimeout(timeout)` | Set default toast timeout duration |
| `close()` | Close the current dialog |
| `destroy()` | Remove all dialogs and clean up event listeners |

## Browser Compatibility

PosAlert is compatible with all modern browsers. For best results, use the latest versions of:

- Chrome
- Firefox
- Safari
- Edge

## License

MIT License
