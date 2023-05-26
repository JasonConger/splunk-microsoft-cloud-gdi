<html>
  <head>
    <script type="text/javascript" src="https://www.gstatic.com/charts/loader.js"></script>
    <script type="text/javascript">
      google.charts.load('current', {'packages':['sankey']});
      google.charts.setOnLoadCallback(drawChart);

      function drawChart() {
        var azure_data = new google.visualization.DataTable();
        azure_data.addColumn('string', 'Resource');
        azure_data.addColumn('string', 'Data Source');
        azure_data.addColumn('number', 'Weight');
        azure_data.addRows([
            // Virtual Machines
            ['Virtual Machine','VM Metrics', 3],
            ['Virtual Machine','VM Metadata', 2],

            ['VM Metrics','Storage Table', 1],
            ['VM Metrics','Azure Monitor Metrics', 1],
            ['VM Metrics','Universal Forwarder', 1],
            ['VM Metadata','Splunk Add-on for Microsoft Azure', 1],
            ['VM Metadata','Splunk Add-on for Microsoft Cloud Services', 1],

            // Diagnostic Logs
            ['Diagnostic Logs','Storage Blob', 1],
            ['Diagnostic Logs','Event Hub', 1],

            // Security Center
            ['Microsoft Defender for Cloud','ASC Alerts', 1],
            ['Microsoft Defender for Cloud','ASC Tasks', 1],

            ['ASC Alerts','Splunk Add-on for Microsoft Azure', 1],
            ['ASC Tasks','Splunk Add-on for Microsoft Azure', 1],
            
            // Azure Monitor
            ['Azure Monitor','Azure Monitor Metrics',1],
            ['Azure Monitor','Azure Monitor Diagnostic Logs',1],
            ['Azure Monitor','Azure Monitor Activity Log',1],
            
            ['Azure Monitor Metrics','Splunk Add-on for Microsoft Azure', 1],
            ['Azure Monitor Metrics','Splunk Add-on for Microsoft Cloud Services', 1],
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
            ['Cost & Billing','Billing Details', 2],
            ['Cost & Billing','Reservation Recommendations', 2],

            ['Billing Details','Splunk Add-on for Microsoft Azure', 1],
            ['Billing Details','Splunk Add-on for Microsoft Cloud Services', 1],
            ['Reservation Recommendations','Splunk Add-on for Microsoft Azure', 1],
            ['Reservation Recommendations','Splunk Add-on for Microsoft Cloud Services', 1],

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
      
        var defender_data = new google.visualization.DataTable();
        defender_data.addColumn('string', 'Resource');
        defender_data.addColumn('string', 'Data Source');
        defender_data.addColumn('number', 'Weight');
      
        defender_data.addRows([
            // Microsoft Defender 365
            ['Microsoft Defender 365','Incidents', 1],
            ['Microsoft Defender 365','Advanced Hunting', 2],
      
            ['Incidents', 'Splunk Add-on for Microsoft Security', 1],
      
            // Microsoft Defender for Endpoint
            ['Microsoft Defender for Endpoint','Alerts',1],
      
            ['Alerts', 'Splunk Add-on for Microsoft Security', 1],
      
            // Microsoft Defender for Office 365
            ['Microsoft Defender for Office 365', 'Splunk Add-on for Microsoft Office 365', 1],
      
            // Microsoft Defender for Cloud Apps
            ['Microsoft Defender for Cloud Apps', 'Splunk Add-on for Microsoft Office 365', 1],
      
            // Microsoft Defender for Cloud
            ['Microsoft Defender for Cloud','Splunk Add-on for Microsoft Azure', 1],
            ['Microsoft Defender for Cloud','Event Hub', 1],
      
            // Advanced Hunting
            ['Advanced Hunting','Event Hub', 1],
            ['Advanced Hunting','Splunk Add-on for Microsoft Security', 1],
      
            // Event Hub
            ['Event Hub','Splunk Add-on for Microsoft Cloud Services', 2]
      
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
        var azure_chart = new google.visualization.Sankey(document.getElementById('azure_sankey'));
        var defender_chart = new google.visualization.Sankey(document.getElementById('defender_sankey'));
      
        google.visualization.events.addListener(azure_chart, 'select', function() {
          var sel = azure_chart.getSelection();
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
      
        google.visualization.events.addListener(defender_chart, 'select', function() {
          var sel = defender_chart.getSelection();
          if (sel.length) {
            switch (sel[0].name) {
              case 'Splunk Add-on for Microsoft Security':
                window.open('https://splunkbase.splunk.com/app/6207');
                break;
              case 'Splunk Add-on for Microsoft Azure':
                window.open('https://splunkbase.splunk.com/app/3757/');
                break;
              case 'Splunk Add-on for Microsoft Cloud Services':
                window.open('https://splunkbase.splunk.com/app/3110/');
                break;
              case 'Splunk Add-on for Microsoft Office 365':
                window.open('https://splunkbase.splunk.com/app/4055/');
                break;
            }
          }
        });
      
        azure_chart.draw(azure_data, options);
        defender_chart.draw(defender_data, options);
      }
    </script>
  </head>
  <body>
    <h1>Getting Cloud data into Splunk</h1>
    <h2>Microsoft Azure</h2>
    <div id="azure_sankey" style="width: 1000px; height: 600px;"></div>
    
    <h2>Microsoft Defender</h2>
    <div id="defender_sankey" style="width: 1000px;"></div>
  </body>
</html>
