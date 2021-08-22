## Installation
You can get the widget using the following methods:
- From the [GitHub repository](https://github.com/year-calendar/js-year-calendar/releases)
- From the Node package manager, using the following command: `npm install js-year-calendar`
- From the CDN, by adding the following script directly in your HTML page: `<script src="https://unpkg.com/js-year-calendar@latest/dist/js-year-calendar.min.js"></script>`

## Usage

You can create a calendar using the following javascript code :
```
new Calendar('.calendar')
```

Or

```
new Calendar(document.querySelector('.calendar'));
```

Where `.calendar` is the selector of a `DIV` element that should contain your calendar.

You can also use the following HTML if you don't want to use javascript to initialize the calendar
```
<div data-provide="calendar"></div>
```
The calendar will be automatically created when the page will finish loading

## Using options

You can specify options to customize the calendar:
```
new Calendar('.calendar', {
    style: 'background',
    minDate: new Date()
})
```

You can find the exhaustive list of options in the [documentation](/documentation).

## Language

If you want to use the calendar in a different language, you should import the locale file corresponding to the language you want to use, and then set the `language` prop of the calendar:

```
import Calendar from 'js-year-calendar';
import 'js-year-calendar/locales/js-year-calendar.fr';
```

OR

```
<script src="https://unpkg.com/js-year-calendar@latest/dist/js-year-calendar.umd.min.js"></script>
<script src="https://unpkg.com/js-year-calendar@latest/locales/js-year-calendar.fr.js"></script>
```

Then

```
new Calendar('.calendar', {
    language: 'fr'
})
```

The list of available languages is available [here](https://github.com/year-calendar/js-year-calendar/tree/master/locales)

## Updating calendar

You can update the calendar after being instantiated:
```
const calendar = new Calendar('.calendar');

calendar.setStyle('background');
calendar.setMaxDate(new Date());
```

You can find the exhaustive list of methods in the [documentation](/documentation).

## Events

You can bind events to the calendar at initialization
```
const calendar = new Calendar('.calendar', {
    clickDay: function(e) {
        alert('Click on day ' + e.date.toString());
    }
});
```

or later

```
new Calendar('.calendar');
document.querySelector('.calendar').addEventListener('clickDay', function(e) {
    alert('Click on day ' + e.date.toString());
});
```

You can find the exhaustive list of events in the [documentation](/documentation).

## Migrating from bootstrap-year-calendar

This widget is based on the [bootstrap-year-calendar](https://github.com/Paul-DS/bootstrap-year-calendar) widget.
If you were using this widget, these are the modifications to apply to successfully migrate your project:

### Initialization

The project doesn't use jQuery anymore, so the initialization of the calendar will be using pure Javascript.

The old code:
```
$('.calendar').calendar({ /* Options */ })
```

Will be replaced by:
```
new Calendar('.calendar', { /* Options */ });
```

Or 

```
new Calendar($('.calendar').get(0), { /* Options */ });
// Use ".get(0)" to get the DOM element from the jQuery element
```

### Get the calendar from the DOM element

Given that the widget doesn't rely on jQuery, it won't be possible to get the calendar instance from the DOM element anymore:
```
$('.calendar').data('calendar').set...();
```

You will have to store the instance of the calendar by yourself:
```
const calendar = new Calendar('.calendar');

...

calendar.set...();
```
