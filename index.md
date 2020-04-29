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
            ['VM Metadata','Microsoft Azure Add-on for Splunk', 1],

            // Diagnostic Logs
            ['Diagnostic Logs','Storage Blob', 1],
            ['Diagnostic Logs','Event Hub', 1],

            // Security Center
            ['Azure Security Center','ASC Alerts', 1],
            ['Azure Security Center','ASC Tasks', 1],

            ['ASC Alerts','Microsoft Azure Add-on for Splunk', 1],
            ['ASC Tasks','Microsoft Azure Add-on for Splunk', 1],
            
            // Azure Monitor
            ['Azure Monitor','Azure Monitor Metrics',1],
            ['Azure Monitor','Azure Monitor Diagnostic Logs',1],
            ['Azure Monitor','Azure Monitor Activity Log',1],
            
            ['Azure Monitor Metrics','Microsoft Azure Add-on for Splunk', 1],
            ['Azure Monitor Diagnostic Logs','Event Hub', 1],
            ['Azure Monitor Activity Log','Event Hub', 1],

            // Azure Websites
            ['Azure Websites','Website Application Logs', 1],
            ['Azure Websites','Website Server Logs', 1],

            ['Website Application Logs','Storage Blob', 1],
            ['Website Server Logs','Storage Blob', 1],

            // Application Insights
            ['Application Insights','Storage Blob', 1],

            // Activity Log
            ['Activity Logs','Event Hub', 1],
            ['Activity Logs','Splunk Add-on for Microsoft Cloud Services', 1],

            // Cost and Consumption
            ['Cost & Billing','Billing Details', 1],
            ['Cost & Billing','Reservation Recommendations', 1],

            ['Billing Details','Microsoft Azure Add-on for Splunk', 1],
            ['Reservation Recommendations','Microsoft Azure Add-on for Splunk', 1],

            // Azure AD
            ['Azure Active Directory','AAD Users', 1],
            ['Azure Active Directory','AAD Sign-ins', 1],
            ['Azure Active Directory','AAD Audit', 1],

            ['AAD Users','Microsoft Azure Add-on for Splunk', 1],
            ['AAD Sign-ins','Microsoft Azure Add-on for Splunk', 1],
            ['AAD Sign-ins','Event Hub', 1],
            ['AAD Audit','Microsoft Azure Add-on for Splunk', 1],
            ['AAD Audit','Event Hub', 1],

            // Network Watcher
            ['Network Watcher','Network Security Group Flow Logs', 1],
            ['Network Watcher','Topology', 1],

            ['Network Security Group Flow Logs','Storage Blob', 1],
            ['Topology','Microsoft Azure Add-on for Splunk', 1],

            // Storage
            ['Storage Table','Splunk Add-on for Microsoft Cloud Services', 1],
            ['Storage Blob','Splunk Add-on for Microsoft Cloud Services', 5],

            // Event Hub
            ['Event Hub','Microsoft Azure Add-on for Splunk', 1],
            ['Event Hub','Azure Functions', 1],
            ['Event Hub','Data Stream Processor', 1]

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
        chart.draw(data, options);
      }
    </script>
  </head>
  <body>
    <h1>Getting Azure data into Splunk</h1>
    <div id="sankey_basic" style="width: 1000px; height: 600px;"></div>
  </body>
</html>
