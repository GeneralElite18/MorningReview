Prompt: How do I get a responsive table in html?

To create a responsive table in HTML, you can use CSS to style the table and make it adapt to different screen sizes. Here's an example of how you can achieve this:

HTML:
```html
<div class="table-wrapper">
  <table>
    <thead>
      <tr>
        <th>Header 1</th>
        <th>Header 2</th>
        <th>Header 3</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td>Data 1</td>
        <td>Data 2</td>
        <td>Data 3</td>
      </tr>
      <!-- Add more rows as needed -->
    </tbody>
  </table>
</div>
```

CSS:
```css
.table-wrapper {
  overflow-x: auto; /* Enable horizontal scrolling */
}

table {
  width: 100%;
  border-collapse: collapse;
}

th, td {
  padding: 8px;
  text-align: left;
  border-bottom: 1px solid #ddd;
}

@media screen and (max-width: 600px) {
  /* Hide table headers and display cells as blocks */
  thead tr {
    position: absolute;
    top: -9999px;
    left: -9999px;
  }

  tbody, tr, td {
    display: block;
    width: 100%;
  }

  td {
    text-align: right;
    padding-left: 50%;
    white-space: nowrap;
  }

  td:before {
    /* Add content of the header before each data cell */
    content: attr(data-label);
    font-weight: bold;
    display: inline-block;
    width: 50%;
    padding-right: 10px;
    text-align: left;
  }
}
```

In the above code, we wrap the table in a `<div>` element with a class of "table-wrapper" to enable horizontal scrolling when the table exceeds the available width. The CSS styles the table and applies media queries to make it responsive.

The media query with `(max-width: 600px)` targets screens with a maximum width of 600 pixels. Inside this media query, we hide the table headers (`<thead>`) by positioning them off-screen. We also set the display of `<tbody>`, `<tr>`, and `<td>` elements to block to make them stack vertically.

To display the header labels for each data cell, we use the `::before` pseudo-element on `<td>` elements. The content of the pseudo-element is set to the `data-label` attribute of each cell, which corresponds to the table header. The `data-label` attribute is added to each `<td>` element in the HTML.

By implementing this HTML and CSS code, your table should become responsive, adapting to different screen sizes and providing a better user experience on smaller devices.