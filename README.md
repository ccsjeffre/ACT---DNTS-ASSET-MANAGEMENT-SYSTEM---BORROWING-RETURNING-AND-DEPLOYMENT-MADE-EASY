# ACT---DNTS-ASSET-MANAGEMENT-SYSTEM---BORROWING-RETURNING-AND-DEPLOYMENT-MADE-EASY
CAPSTONE 2


#SCAFFOLD
Scaffold-DbContext "Data Source=YourServerName;Initial Catalog=YourDBName;Integrated Security=True;Trust Server Certificate=True;" Microsoft.EntityFrameworkCore.SqlServer -OutputDir Models -ContextDir Context -Context MyDBContext -f

#APPSETTINGS.JSON
"ConnectionStrings": {
    "Default": "Data Source=YourServerName;Initial Catalog=YourDBName;Integrated Security=True;Trust Server Certificate=True;"
}


#PROGRAM.CS
builder.Services.AddDbContext<MyDBContext>(options =>
    options
        .UseSqlServer(builder.Configuration.GetSection("ConnectionStrings:Default").Value,
            sql => sql.EnableRetryOnFailure())
        .EnableSensitiveDataLogging(), 
    ServiceLifetime.Transient
);

