# utl_driving_distance_from_city_to_city_using_google_maps
Driving distance and time from city to city using google maps. Keywords: sas sql join merge big data analytics macros oracle teradata mysql sas communities stackoverflow statistics artificial inteligence AI Python R Java Javascript WPS Matlab SPSS Scala Perl C C# Excel MS Access JSON graphics maps NLP natural language processing machine learning igraph DOSUBL DOW loop stackoverfl SAS community.
    Driving distance from city to city using google maps

    https://developers.google.com/maps/documentation/javascript/usage

    "Most websites and applications may use the standard Google Maps JavaScript API free of charge. 
    A project is restricted to the complimentary per-day-limit of 25,000 map loads, unless you enable billing on the project." 

    You do not need a Google API for this.

    github
    https://github.com/rogerjdeangelis/utl_driving_distance_from_city_to_city_using_google_maps

    SAS Forum
    https://tinyurl.com/ycfrjtzv
    https://communities.sas.com/t5/Base-SAS-Programming/SAS-Google-Maps-drive-distance-time-any-info-on-what-the/m-p/449060

    Doc on R and google maps
    https://cran.r-project.org/web/packages/gmapsdistance/README.html


    INPUT  Two macro variables
    ==========================

       %let origin="Washington+DC";
       %let destination="New+York+City+NY";


    PROCESS (working code)
    =======================

      results = gmapsdistance(origin = &origin, destination = &destination, mode = "driving");
      driving_miles=(results$Distance/1000)*.621371; * meters to miles;

    OUTPUT
    ======

     WORK.WANTWPS total obs=1

        DRIVING_
          MILES
         224.908

    *                _              _       _
     _ __ ___   __ _| | _____    __| | __ _| |_ __ _
    | '_ ` _ \ / _` | |/ / _ \  / _` |/ _` | __/ _` |
    | | | | | | (_| |   <  __/ | (_| | (_| | || (_| |
    |_| |_| |_|\__,_|_|\_\___|  \__,_|\__,_|\__\__,_|

    ;

    %let origin="Washington+DC";
    %let destination="New+York+City+NY";

    *          _       _   _
     ___  ___ | |_   _| |_(_) ___  _ __
    / __|/ _ \| | | | | __| |/ _ \| '_ \
    \__ \ (_) | | |_| | |_| | (_) | | | |
    |___/\___/|_|\__,_|\__|_|\___/|_| |_|

    ;

    %utl_submit_wps64('
    options set=R_HOME "C:/Program Files/R/R-3.3.2";
    libname wrk sas7bdat "%sysfunc(pathname(work))";
    proc r;
    submit;
    source("C:/Program Files/R/R-3.3.2/etc/Rprofile.site", echo=T);
    library(gmapsdistance);
    results = gmapsdistance(origin = &origin,
       destination = &destination,
       mode = "driving");
    results;
    driving_miles=(results$Distance/1000)*.621371;
    endsubmit;
    import r=driving_miles data=wrk.wantwps;
    run;quit;
    ');


    > source("C:/Program Files/R/R-3.3.2/etc/Rprofile.site", echo=T)
    > .libPaths(c(.libPaths(), "d:/3.3.2", "d:/3.3.2_usr"))
    > options(help_type = "html")
    > library(gmapsdistance)
    > results = gmapsdistance(origin = "Washington+DC",   destination = "New+York+City+NY",   mode = "driving")
    > results
    > driving_miles=(results$Distance/1000)*.621371

    NOTE: Processing of R statements complete

    11        import r=driving_miles data=wrk.wantwps;
    NOTE: Creating data set 'WRK.wantwps' from R data frame 'driving_miles'
    NOTE: Column names modified during import of 'driving_miles'
    NOTE: Data set "WRK.wantwps" has 1 observation(s) and 1 variable(s)

    12        run;
    NOTE: Procedure r step took :
          real time : 1.450
          cpu time  : 0.046


    13        quit;

