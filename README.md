<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <title>Corona Api</title>
    <style>
        body {
            background-image: url("covid.jpg");
            background-size: ;
        }
        
        table {
            background: white;
            border-radius: 10px;
            padding: 7px;
        }
        
        #global-wise th {
            background: red;
            color: white;
        }
        
        .search {
            float: right;
            margin-right: 138px;
            width: ;
        }
    </style>
</head>

<body>
    <!-- global data -->
    <table border="1px" cellspacing="0" cellpadding="10px" width="40%" align="center" id="global-wise" bgcolor="silver">
        <tr>
            <th colspan="2">GLOBAL DATA</th>
        </tr>
        <tbody id="global-data">

        </tbody>
    </table><br><br>

    <table class="search">
        <tr id="search-input">
            <td>Search : </td>
            <td><input type="text" id="search" name="" autocomplete=off placeholder="Search By Country"></td>
        </tr>
    </table><br><br><br><br>

    <!-- countries data -->
    <table border="1px" cellspacing="0" cellpadding="10px" width="80%" align="center" id="country-wise" bgcolor="gray">
        <tr>
            <th colspan="8" bgcolor="red">COUNTRIES DATA</th>
        </tr>

        <tbody id="country-data">
            <tr bgcolor="yellow">
                <th>Sr.No</th>
                <th>Country</th>
                <th>NewConfirmed</td>
                    <th>TotalConfirmed</th>
                    <th>NewDeaths</th>
                    <th>TotalDeaths</td>
                        <th>NewRecovered</th>
                        <th>TotalRecovered</th>
            </tr>
        </tbody>
    </table>
    <script src="js/jquery-3.5.1.js"></script>
    <script>
        $.ajax({
            url: "https://api.covid19api.com/summary",
            type: "GET",
            dataType: "JSON",
            success: function(data) {
                console.log(data.Countries);
                $.each(data.Global, function(key, value) {
                    $("#global-data").append("<tr><td>" + key + "</td><td  align='center'>" + value + "</td></tr>");
                })
                var srno = 1
                $.each(data.Countries, function(key, value) {
                    $("#country-data").append("<tr>" +
                        "<td>" + srno + "</td>" +
                        "<td>" + value.Country + "</td>" +
                        "<td>" + value.NewConfirmed + "</td>" +
                        "<td>" + value.TotalConfirmed + "</td>" +
                        "<td>" + value.NewDeaths + "</td>" +
                        "<td>" + value.TotalDeaths + "</td>" +
                        "<td>" + value.NewRecovered + "</td>" +
                        "<td>" + value.TotalRecovered + "</td>" +
                        "</tr>");

                    srno++;
                })

            }
        })
    </script>
</body>

</html>
