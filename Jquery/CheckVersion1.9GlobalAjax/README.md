Jquery는 1.9사용하기 전 체크
====================

# 1. Jquery 1.9
Jquery 1.9부터는 기존 버전에서 동작햇었던 기능 몇개가 변화 했고 그중 하나가 AjaxGlobal API입니다.
## 1.1 변경점
1.9 이상부터는 더이상 아래와 같이 사용 할 수가 없습니다.

    $('log').ajaxStart(function() { // 1.9이상부터는 이렇게 사용 불가능
      $( "#loading" ).show();
    });
    
    $(document).ajaxStart(function() { // 1.9이상부터는 이렇게 사용해야한다.
        $( "#loading" ).show();
    });
    
## 1.2 기존 버전 호환
1.9이전 호환을 위해서 사용해야 한다면 jquery-migrate.js를 사용해야 합니다.

    <!DOCTYPE html>
    <html lang="en">
    <head>
        <meta charset="UTF-8">
        <title>1.9.0 이상의 jquery 사용시 global ajax통신 체크 필요</title>
        <script src="jquery-1.10.2.js" ></script>
        <script src="jquery-migrate-1.2.1.min.js" ></script>
    
        <script>
            $(document).ready(function() {
                // Jquery 1.9.0 버전 이상부터는 더이상 $().ajaxStart()이나 $(특정엘리먼트).ajaxStart()가 동작하지 않게 설계가 되어 있습니다.
                // 하지만 jquery-migrate.js를 사용하면 기존 1.9이전의 기능도 사용할 수 잇게 되죠. 즉 이것은 이전 버전의 호환성으로 인해서 만들어지게 되었습니다.
                $(".log").ajaxStart(function() { // 1.9.0이전버전에서만 동작함. 아니면 jquery-migrate를 사용하던가 해야합니다.
                    $( ".log" ).text( "Triggered ajaxStart handler." );
                });
    
                $(".trigger").click(function() {
                    $(".result").load("test.html");
                });
            });
        </script>
    </head>
    <body>
        <div class="trigger">Trigger</div>
        <div class="result"></div>
        <div class="log"></div>
    </body>
    </html>

## 1.3 정리

1. 1.9부턴 $('log').ajaxStart()같은 글로벌 api를 사용할수 없습니다. 
2. $('log').ajaxStart()를 사용하려면 jquery-migrate.js를 추가 해서 사용하시길 바랍니다.