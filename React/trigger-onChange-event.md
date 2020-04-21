# Trigger custom `onChange` event
> 21/04/2020 | working on Adobe Panorama project

### Problem Statement
Wanted to add [daterangepicker](https://www.daterangepicker.com/) in a react project. 
Added the necessary script and link tags in `public/index.html`, and got the basic thing working.
But when I select a date range, `onChange` event in React's Form was not invoked.

### Solution
- Use `react-trigger-change` library [[source]](https://stackoverflow.com/a/45356934/13218539)
- In index.html
  ```javascript
  <script type="text/javascript" src="https://cdn.jsdelivr.net/jquery/latest/jquery.min.js"></script>
  <script type="text/javascript" src="https://cdn.jsdelivr.net/momentjs/latest/moment.min.js"></script>
  <script type="text/javascript" src="https://cdn.jsdelivr.net/npm/daterangepicker/daterangepicker.min.js"></script>
  <script type="text/javascript" src="https://unpkg.com/react-trigger-change/dist/react-trigger-change.js"></script>
  <link rel="stylesheet" type="text/css" href="https://cdn.jsdelivr.net/npm/daterangepicker/daterangepicker.css" />

  <script>
    $(function() {
      $('#date-search-key').daterangepicker({
        opens: 'left'
      }, function(start, end, label) {
        const element = document.getElementById('date-search-key');
        element.value = start + ' - ' + end;
        reactTriggerChange(element);
      });
    });
  </script>
  ```
