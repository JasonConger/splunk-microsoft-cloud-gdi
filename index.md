<html>
  <head>
    <script type="text/javascript" src="https://www.gstatic.com/charts/loader.js"></script>
    <script type="text/javascript">
      google.charts.load('current', {'packages':['sankey']});
      google.charts.setOnLoadCallback(drawChart);

      function drawChart() {
        var data = new google.visualization.DataTable();
        data.addColumn('string', 'Resource');
        data.addColumn('string', 'Data Source');
        data.addColumn('number', 'Weight');
        data.addRows([
            // Virtual Machines
            ['Virtual Machine','VM Metrics', 3],
            ['Virtual Machine','VM Metadata', 1],

            ['VM Metrics','Storage Table', 1],
            ['VM Metrics','Azure Monitor Metrics', 1],
            ['VM Metrics','Universal Forwarder', 1],
            ['VM Metadata','Splunk Add-on for Microsoft Azure', 1],

            // Diagnostic Logs
            ['Diagnostic Logs','Storage Blob', 1],
            ['Diagnostic Logs','Event Hub', 1],

            // Security Center
            ['Azure Security Center','ASC Alerts', 1],
            ['Azure Security Center','ASC Tasks', 1],

            ['ASC Alerts','Splunk Add-on for Microsoft Azure', 1],
            ['ASC Tasks','Splunk Add-on for Microsoft Azure', 1],
            
            // Azure Monitor
            ['Azure Monitor','Azure Monitor Metrics',1],
            ['Azure Monitor','Azure Monitor Diagnostic Logs',1],
            ['Azure Monitor','Azure Monitor Activity Log',1],
            
            ['Azure Monitor Metrics','Splunk Add-on for Microsoft Azure', 2],
            ['Azure Monitor Diagnostic Logs','Event Hub', 1],
            ['Azure Monitor Activity Log','Event Hub', 1],

            // Azure Websites
            ['Azure Websites','Website Application Logs', 1],
            ['Azure Websites','Website Server Logs', 1],

            ['Website Application Logs','Storage Blob', 1],
            ['Website Server Logs','Storage Blob', 1],

            // Application Insights
            ['Application Insights','Storage Blob', 1],
            ['Application Insights','Event Hub', 1],

            // Activity Log
            ['Activity Logs','Event Hub', 1],
            ['Activity Logs','Splunk Add-on for Microsoft Cloud Services', 1],
            ['Activity Logs','Splunk Data Manager (cloud only)', 1],

            // Cost and Consumption
            ['Cost & Billing','Billing Details', 1],
            ['Cost & Billing','Reservation Recommendations', 1],

            ['Billing Details','Splunk Add-on for Microsoft Azure', 1],
            ['Reservation Recommendations','Splunk Add-on for Microsoft Azure', 1],

            // Azure AD
            ['Azure Active Directory','AAD Users', 1],
            ['Azure Active Directory','AAD Sign-ins', 3],
            ['Azure Active Directory','AAD Audit', 3],
            ['Azure Active Directory','AAD Devices', 1],
            ['Azure Active Directory','AAD Risk Detection', 1],

            ['AAD Users','Splunk Add-on for Microsoft Azure', 1],
            ['AAD Sign-ins','Splunk Add-on for Microsoft Azure', 1],
            ['AAD Sign-ins','Splunk Data Manager (cloud only)', 1],
            ['AAD Devices','Splunk Add-on for Microsoft Azure', 1],
            ['AAD Risk Detection','Splunk Add-on for Microsoft Azure', 1],
            ['AAD Sign-ins','Event Hub', 1],
            ['AAD Audit','Splunk Add-on for Microsoft Azure', 1],
            ['AAD Audit','Splunk Data Manager (cloud only)', 1],
            ['AAD Audit','Event Hub', 1],

            // Network Watcher
            ['Network Watcher','Network Security Group Flow Logs', 1],
            ['Network Watcher','Topology', 1],

            ['Network Security Group Flow Logs','Storage Blob', 1],
            ['Topology','Splunk Add-on for Microsoft Azure', 1],

            // Storage
            ['Storage Table','Splunk Add-on for Microsoft Cloud Services', 1],
            ['Storage Blob','Splunk Add-on for Microsoft Cloud Services', 5],

            // Event Hub
            ['Event Hub','Splunk Add-on for Microsoft Cloud Services', 4],
            ['Event Hub','Azure Functions', 3],

        ]);

        // Sets chart options.
        var options = {
            sankey: {
                node: {
                    interactivity: true,
                }
            },
            tooltip : {
                trigger: 'focus'
            }
        };

        // Instantiates and draws our chart, passing in some options.
        var chart = new google.visualization.Sankey(document.getElementById('sankey_basic'));
        google.visualization.events.addListener(chart, 'select', function() {
          var sel = chart.getSelection();
          if (sel.length) {
            switch (sel[0].name) {
              case 'Universal Forwarder':
                window.open('https://docs.splunk.com/Documentation/Forwarder/latest/Forwarder/Abouttheuniversalforwarder');
                break;
              case 'Splunk Add-on for Microsoft Azure':
                window.open('https://splunkbase.splunk.com/app/3757/');
                break;
              case 'Splunk Add-on for Microsoft Cloud Services':
                window.open('https://splunkbase.splunk.com/app/3110/');
                break;
              case 'Azure Functions':
                window.open('https://github.com/splunk/azure-functions-splunk/tree/master/event-hubs-hec');
                break;
              case 'Splunk Data Manager (cloud only)':
                window.open('https://docs.splunk.com/Documentation/DM');
                break;
            }
          }
        });
        chart.draw(data, options);
      }
    </script>
  </head>
  <body>
    <h1>Getting Azure data into Splunk</h1>
    <div id="sankey_basic" style="width: 1000px; height: 600px;"></div>
  </body>
</html>
