---
hide:
  - toc
---


# Data

<table>
  <thead>
    <tr>
    {%- for c in get_table_headers() %}
      <th>{{ c }}</th>
    {%- endfor %}
    </tr>
  </thead>
  <tbody></tbody>
</table>

<link href="https://cdn.datatables.net/v/dt/jq-3.7.0/jszip-3.10.1/dt-2.1.7/b-3.1.2/b-colvis-3.1.2/b-html5-3.1.2/date-1.5.4/sb-1.8.0/datatables.min.css" rel="stylesheet">
 
<script src="https://cdn.datatables.net/v/dt/jq-3.7.0/jszip-3.10.1/dt-2.1.7/b-3.1.2/b-colvis-3.1.2/b-html5-3.1.2/date-1.5.4/sb-1.8.0/datatables.min.js"></script>  

<script>
  $(document).ready(function() {
    data = {{ get_table_rows() }}
    console.log('test')

    $('table').DataTable({
      data: data,
      columnDefs: [
        { targets: [0, 1, 2, 5, 6], visible: true},
        { targets: '_all', visible: false }
      ],
      layout: {
          top1: 'searchBuilder',
          topStart: {
              buttons: [
                  {
                      extend: 'colvis',
                      postfixButtons: ['colvisRestore']
                  },
                  {
                    extend: 'excelHtml5',
                    autoFilter: true,
                    sheetName: 'Exported data'
                  }
              ]
          }
      }
    });
  });
</script>

<script async defer src="https://scripts.simpleanalyticscdn.com/latest.js"></script>
<noscript><img src="https://queue.simpleanalyticscdn.com/noscript.gif" alt="" referrerpolicy="no-referrer-when-downgrade" /></noscript>