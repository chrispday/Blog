In web.config

	<system.web>
		<httpHandlers>
      <add path="*" verb="OPTIONS" type="System.Web.DefaultHttpHandler" validate="true"/>
			<add verb="*" path="*.asmx" type="System.Web.Script.Services.ScriptHandlerFactory" validate="false" />
		</httpHandlers>
	</system.web>
	
In Global.asax
	
        public void Application_BeginRequest(object sender, EventArgs e)
        {
            // Fires at the beginning of each request
           HttpContext.Current.Response.AppendHeader("Access-Control-Allow-Origin", "*");
           HttpContext.Current.Response.AppendHeader("Access-Control-Allow-Methods", "GET,PUT,POST,DELETE,OPTIONS");
           HttpContext.Current.Response.AppendHeader("Access-Control-Allow-Headers", "Content-Type,Authorization");
        }
