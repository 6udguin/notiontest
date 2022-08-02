# naver api + gov api

부산 영도구 관광정보 API

Response code: 200 → success

결과: <?xml version=”1.0” encoding=”UTF-8” … → success

에러:

javax.servlet.jsp.JspTagException: Don't know how to iterate over supplied "items" in <forEach>

→ List구조가 아닌데, c:forEach반복문을 사용해 일어나는 에러. 

<c:forEach>를 빼고 실행하면 에러없이 동작. 

json → object : html로 가져와 < > 에러 

json → obejct x : 값 잘 가져온다. List가 아니여서 <c:forEach>문에서 에러

- json → object
    
    > 코드
    > 
    
    ```java
    // json -> object
    		ObjectMapper om = new ObjectMapper();
    		SearchBusanYDVo vo = null;
    		try {
    			vo = om.readValue(responseBody, SearchBusanYDVo.class);
    		} catch (JsonMappingException e) {
    			// TODO Auto-generated catch block
    			e.printStackTrace();
    		} catch (JsonProcessingException e) {
    			// TODO Auto-generated catch block
    			e.printStackTrace();
    		}
    ```
    
    > 에러
    > 
    - 에러내용
        
        ```python
        SearchController busanYD=10
        Response code: 200
        SearchServiceImpl get, apiUrl=http://openapi.yeongdo.go.kr:8081/openapi-data/service/rest/tour/list?serviceKeyVVYz4W%2BGHKMfPgAWB%2FNEJ0pWPvbjfbjo2k92wTKBbcYMKQQN566vxUAr3QmK7XErBUhhsfp%2BJKu2O3AYiGjECg%3D%3D&numOfRows=10&pageNo=1&addr=&title=, requestHeaders={Content-Type=application/json}
        HttpURLConeection apiUrl=http://openapi.yeongdo.go.kr:8081/openapi-data/service/rest/tour/list?serviceKeyVVYz4W%2BGHKMfPgAWB%2FNEJ0pWPvbjfbjo2k92wTKBbcYMKQQN566vxUAr3QmK7XErBUhhsfp%2BJKu2O3AYiGjECg%3D%3D&numOfRows=10&pageNo=1&addr=&title=
        com.fasterxml.jackson.core.JsonParseException: Unexpected character ('<' (code 60)): expected a valid value (JSON String, Number, Array, Object or token 'null', 'true' or 'false')
         at [Source: (String)"<?xml version="1.0" encoding="UTF-8" standalone="yes"?><response><header><resultCode>00</resultCode><resultMsg>NORMAL SERVICE.</resultMsg></header><body><items><item><address>부산시 영도구 대교동 1가 190-1</address><assetage></assetage><assetdate></assetdate><assetnumber></assetnumber><assetscale></assetscale><category></category><content>길이 214.63m, 너비 18.3m, 높이 7.2m이며, 일제강점기인 1931년에 공사를 시작하여 1934년 11월 23일 준공하였으며 옛날 시청자리 남쪽에서 영도의 북서단을 연결하는 국내 최초의 연륙교이자 유일한 일엽식 도개교로서 일제가 대륙 침략을 위한 보급 및 수송로 구축의 일환으로 건설되었습니"[truncated 12725 chars]; line: 1, column: 2]
        	at com.fasterxml.jackson.core.JsonParser._constructError(JsonParser.java:1922)
        	at com.fasterxml.jackson.core.base.ParserMinimalBase._reportError(ParserMinimalBase.java:710)
        	at com.fasterxml.jackson.core.base.ParserMinimalBase._reportUnexpectedChar(ParserMinimalBase.java:635)
        	at com.fasterxml.jackson.core.json.ReaderBasedJsonParser._handleOddValue(ReaderBasedJsonParser.java:1952)
        	at com.fasterxml.jackson.core.json.ReaderBasedJsonParser.nextToken(ReaderBasedJsonParser.java:781)
        	at com.fasterxml.jackson.databind.ObjectMapper._initForReading(ObjectMapper.java:4682)
        	at com.fasterxml.jackson.databind.ObjectMapper._readMapAndClose(ObjectMapper.java:4584)
        	at com.fasterxml.jackson.databind.ObjectMapper.readValue(ObjectMapper.java:3546)
        	at com.fasterxml.jackson.databind.ObjectMapper.readValue(ObjectMapper.java:3514)
        	at com.basic.search.service.impl.SearchServiceImpl.SearchBusanYD(SearchServiceImpl.java:598)
        	at com.basic.search.controller.SearchController.busanYDSearch(SearchController.java:234)
        	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
        	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:62)
        	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
        	at java.lang.reflect.Method.invoke(Method.java:498)
        	at org.springframework.web.method.support.InvocableHandlerMethod.doInvoke(InvocableHandlerMethod.java:220)
        	at org.springframework.web.method.support.InvocableHandlerMethod.invokeForRequest(InvocableHandlerMethod.java:134)
        	at org.springframework.web.servlet.mvc.method.annotation.ServletInvocableHandlerMethod.invokeAndHandle(ServletInvocableHandlerMethod.java:116)
        	at org.springframework.web.servlet.mvc.method.annotation.RequestMappingHandlerAdapter.invokeHandlerMethod(RequestMappingHandlerAdapter.java:827)
        	at org.springframework.web.servlet.mvc.method.annotation.RequestMappingHandlerAdapter.handleInternal(RequestMappingHandlerAdapter.java:738)
        	at org.springframework.web.servlet.mvc.method.AbstractHandlerMethodAdapter.handle(AbstractHandlerMethodAdapter.java:85)
        	at org.springframework.web.servlet.DispatcherServlet.doDispatch(DispatcherServlet.java:963)
        	at org.springframework.web.servlet.DispatcherServlet.doService(DispatcherServlet.java:897)
        	at org.springframework.web.servlet.FrameworkServlet.processRequest(FrameworkServlet.java:970)
        	at org.springframework.web.servlet.FrameworkServlet.doPost(FrameworkServlet.java:872)
        	at javax.servlet.http.HttpServlet.service(HttpServlet.java:681)
        	at org.springframework.web.servlet.FrameworkServlet.service(FrameworkServlet.java:846)
        	at javax.servlet.http.HttpServlet.service(HttpServlet.java:764)
        	at org.apache.catalina.core.ApplicationFilterChain.internalDoFilter(ApplicationFilterChain.java:227)
        	at org.apache.catalina.core.ApplicationFilterChain.doFilter(ApplicationFilterChain.java:162)
        	at org.apache.tomcat.websocket.server.WsFilter.doFilter(WsFilter.java:53)
        	at org.apache.catalina.core.ApplicationFilterChain.internalDoFilter(ApplicationFilterChain.java:189)
        	at org.apache.catalina.core.ApplicationFilterChain.doFilter(ApplicationFilterChain.java:162)
        	at org.springframework.web.filter.CharacterEncodingFilter.doFilterInternal(CharacterEncodingFilter.java:197)
        	at org.springframework.web.filter.OncePerRequestFilter.doFilter(OncePerRequestFilter.java:107)
        	at org.apache.catalina.core.ApplicationFilterChain.internalDoFilter(ApplicationFilterChain.java:189)
        	at org.apache.catalina.core.ApplicationFilterChain.doFilter(ApplicationFilterChain.java:162)
        	at com.navercorp.lucy.security.xss.servletfilter.XssEscapeServletFilter.doFilter(XssEscapeServletFilter.java:36)
        	at org.apache.catalina.core.ApplicationFilterChain.internalDoFilter(ApplicationFilterChain.java:189)
        	at org.apache.catalina.core.ApplicationFilterChain.doFilter(ApplicationFilterChain.java:162)
        	at org.apache.catalina.core.StandardWrapperValve.invoke(StandardWrapperValve.java:197)
        	at org.apache.catalina.core.StandardContextValve.invoke(StandardContextValve.java:97)
        	at org.apache.catalina.authenticator.AuthenticatorBase.invoke(AuthenticatorBase.java:541)
        	at org.apache.catalina.core.StandardHostValve.invoke(StandardHostValve.java:135)
        	at org.apache.catalina.valves.ErrorReportValve.invoke(ErrorReportValve.java:92)
        	at org.apache.catalina.valves.AbstractAccessLogValve.invoke(AbstractAccessLogValve.java:687)
        	at org.apache.catalina.core.StandardEngineValve.invoke(StandardEngineValve.java:78)
        	at org.apache.catalina.connector.CoyoteAdapter.service(CoyoteAdapter.java:360)
        	at org.apache.coyote.http11.Http11Processor.service(Http11Processor.java:399)
        	at org.apache.coyote.AbstractProcessorLight.process(AbstractProcessorLight.java:65)
        	at org.apache.coyote.AbstractProtocol$ConnectionHandler.process(AbstractProtocol.java:890)
        	at org.apache.tomcat.util.net.NioEndpoint$SocketProcessor.doRun(NioEndpoint.java:1787)
        	at org.apache.tomcat.util.net.SocketProcessorBase.run(SocketProcessorBase.java:49)
        	at org.apache.tomcat.util.threads.ThreadPoolExecutor.runWorker(ThreadPoolExecutor.java:1191)
        	at org.apache.tomcat.util.threads.ThreadPoolExecutor$Worker.run(ThreadPoolExecutor.java:659)
        	at org.apache.tomcat.util.threads.TaskThread$WrappingRunnable.run(TaskThread.java:61)
        	at java.lang.Thread.run(Thread.java:748)
        <?xml version="1.0" encoding="UTF-8" standalone="yes"?><response><header><resultCode>00</resultCode><resultMsg>NORMAL SERVICE.</resultMsg></header><body><items><item><address>부산시 영도구 대교동 1가 190-1</address><assetage></assetage><assetdate></assetdate><assetnumber></assetnumber><assetscale></assetscale><category></category><content>길이 214.63m, 너비 18.3m, 높이 7.2m이며, 일제강점기인 1931년에 공사를 시작하여 1934년 11월 23일 준공하였으며 옛날 시청자리 남쪽에서 영도의 북서단을 연결하는 국내 최초의 연륙교이자 유일한 일엽식 도개교로서 일제가 대륙 침략을 위한 보급 및 수송로 구축의 일환으로 건설되었습니다. 당시로서는 최초라 할수 있는 도개교로써 하루 7차례씩 영도대교 아래를 지나는 선박을 위해 다리가 들어올려지는 장관을 연출, 부산 최고의 명물로 손꼽혔으나 영도의 인구증가 및 교통난등으로 인하여 1966년 9월 1일 그 들림 기능이 중단되게 되었지만 한국 근현대사의 상징적 건축물로 평가되어 2006년 11월 25일 부산광역시 기념물 제56호로 지정되었고 2013년 11월 27일 기존 4차선 도로를 6차선으로 확장 및 도개기능 복원을 통해 다시금 부산의 명물로 옛 명성을 다시 찾고 있습니다.&#xD;&#xD;&#xD;▣ 기타정보&#xD;&#xD;* 영도다리축제: 부산의 근대문화유산이자 영도구민의 삶과 애환을 함께 해 온 영도다리를 소재로 한 전국 유일의 다리축제로서, 47년만에 도개교로 다시 태어난 영도다리의 가치를 재조명하고 영도의 대표적 문화관광자원으로 널리 알리기 위해 매년 9‧10월 개최 하고 있습니다.&#xD;&#xD;&#xD;&#xD;&#xD;&#xD;</content><copy></copy><course></course><etc></etc><fee>없음</fee><food></food><guide></guide><homepage></homepage><idx>2158</idx><institution></institution><islandName></islandName><manage>영도구청</manage><map>◾지하철 1호선 남포역에 하차 후 6번 출구.&#xD;&#xD;◾출발지: 부산역 → 88A 탑승 후 영도경찰서 정류장에 하차.</map><multifileId>MF00000151</multifileId><multifileIdx>25121</multifileIdx><name>영도대교</name><parking>없음</parking><phone>051-419-4064</phone><product>/02164.web?gcode=1190&amp;idx=11240&amp;amode=view&amp;</product><sightseeing></sightseeing><source></source><trafficinfo></trafficinfo><usehour>* 코로나19로 도개행사 잠정중지 : 2020 .2 .25.~상황안정 시까지&#xD;* 도개시설 시운전 및 안전점검 : 월2회(둘째·넷째 수요일, 14:00~14:20)</usehour><xposition>35.09553006563672</xposition><yposition>129.03645177617253</yposition></item><item><address>부산광역시 영도구 전망로 209 (동삼동) </address><assetage></assetage><assetdate>2005년 11월 01일</assetdate><assetnumber>명승 제17호</assetnumber><assetscale></assetscale><category></category><content>태종대는 신라 29대 임금이자 삼국통일의 초석을 다진 태종무열왕(김춘추)이 전국을 순회하던 도중 울창한 소나무 숲과 삼면이 바다로 둘러싸인 기암절벽 등 이곳의 빼어난 해안 절경에 심취해 활을 쏘며 즐긴 것에서 유래한 명칭입니다.&#xD;영도해안을 따라 약 9.1㎞의 최남단에 위치하고 있는 태종대는 1,713,763㎡ 면적에 해발 250m의 최고봉을 중심으로 해송을 비롯한 120여종의 수목이 울창하게 우거져 있으며, 해안에는 깎아 세운 듯한 절벽과 기암괴석 그리고 탁 트인 대한해협을 한눈에 볼 수 있는 명소로 옛부터 많은 국내외 관광객들의 발길이 끊이지 않고 있습니다. 청명한 날에는 약 56㎞거리인 일본의 쓰시마섬까지 볼 수 있어 부산을 대표하는 관광명소로 옛부터 시민과 방문객들이 즐겨 찾았던 곳입니다. 또한 새해 일출을 보기위해 많은 사람들이 방문하는 만큼 새해의 일출을 보기에도 정말 적합한 장소입니다.&#xD;&#xD;&#xD;▣ 시설정보&#xD;&#xD;* 다누비 열차: 매표시간 9:00~17:30/운행시간 09:20~17:30&#xD;(2021. 4. 1. 운행시간 변경 예정   성수기(5월 ~ 9월) : 09:00 ~ 20:00 / 비수기 : 09:00 ~ 18:00 / 정기휴무 : 매주 월요일)&#xD;&#xD;* 해상유람선: 시원한 바닷바람과 유람선의 여유로움을 맛보기에 좋은 장소 입니다. (등대유람선, 태원유람선 등)&#xD;&#xD;* 태종대 전망대 : 태종대 전망대는 푸른 바다와 해안 절경, 그리고 멀리 대한해협을 한눈에 바라볼 수 있는 곳으로, 총 3개 층으로 구성되어 있습니다. 이 중 일부 개장하는 곳은 태종대의 사계절을 테마로 한 2층 매점과 피크닉&amp;태종대 콘셉트로 해안 절경을 바라보며 베이커리와 차를 즐길 수 있는 3층 오션뷰 카페로 운영됩니다.&#xD;&#xD;&#xD;▣ 기타정보&#xD;&#xD;* 도심공원 체험승마 : 승마체험 및 영도 말 관련 스토리텔링 내용 포함(문의전화: 051-860-7866)&#xD;&#xD;* 휠체어 및 유모차 이용 가능(태종대관광안내소), 문의전화 : 051-405-2004&#xD;&#xD;&#xD;&#xD;그 외 자세한 정보는 http://taejongdae.bisco.or.kr/에서 자세히 확인 하실 수 있습니다.&#xD;&#xD;&#xD;&#xD;</content><copy></copy><course></course><etc></etc><fee>무료(다누비 열차 이용요금 : 어른 3,000원, 청소년 2,000원, 어린이 1,500원)</fee><food></food><guide></guide><homepage>http://taejongdae.bisco.or.kr/</homepage><idx>2159</idx><institution></institution><islandName></islandName><manage>태종대유원지사업소</manage><map>◾출발지 : 영도대교 → 88A, 30, 8, 101번 탑승 후 태종대 정류장에서 하차.&#xD;&#xD;◾출발지 : 부산역 → 101번 탑승후 태종대 정류장에서 하차.</map><multifileId>MF00000182</multifileId><multifileIdx>26019</multifileIdx><name>태종대</name><parking>태종대 유원지 입구 주변 주차장 5개소 1,008면&#xD;대형버스 26면, 소형 957면, 장애인 25면</parking><phone>051-405-2004</phone><product>/02164.web?gcode=1190&amp;idx=11237&amp;amode=view&amp;</product><sightseeing></sightseeing><source></source><trafficinfo></trafficinfo><usehour>연중무휴</usehour><xposition>35.0503938134</xposition><yposition>129.0883721702</yposition></item><item><address>부산광역시 영도구 태종로 808 (동삼동) </address><assetage></assetage><assetdate></assetdate><assetnumber></assetnumber><assetscale></assetscale><category></category><content>천혜의 절경을 자랑하는 태종대에 인접하여 온천과 산, 바다, 공원을 함께 즐길 수 있는 곳이다. 노천탕에서 별을 보며 온천을 즐기다 보면 하루의 피곤함이 사라질 것이다. &#xD;</content><copy></copy><course></course><etc></etc><fee></fee><food></food><guide></guide><homepage></homepage><idx>2299</idx><institution></institution><islandName></islandName><manage></manage><map></map><multifileId>MF00001130</multifileId><multifileIdx>26550</multifileIdx><name>태종대 온천</name><parking></parking><phone>051-404-9001</phone><product></product><sightseeing></sightseeing><source></source><trafficinfo></trafficinfo><usehour></usehour><xposition></xposition><yposition></yposition></item><item><address>부산광역시 영도구 동삼동 산 149-4</address><assetage></assetage><assetdate></assetdate><assetnumber></assetnumber><assetscale></assetscale><category></category><content>1975년 완공 되었다 하여 이름 붙여진 75광장은 바다 쪽을 바라 볼 수 있는 정자가 마련되어 있어 조용히 휴식하기에 좋은 공간입니다. &#xD;해안산책로와 연결 되어 있어 산책 하기엔 알맞은 곳으로써, 특히 밤에 달빛이 비치는 밤바다를 바라 보면 아름다움이 절로 느껴지는 곳이기도 합니다.&#xD;</content><copy></copy><course></course><etc></etc><fee>무료</fee><food></food><guide></guide><homepage></homepage><idx>2164</idx><institution></institution><islandName></islandName><manage></manage><map>◾출발지: 영도대교 → 7, 508, 71, 70번 탑승 후 75광장 정류장 하차. &#xD;&#xD;◾출발지: 부산역 → 508번 탑승 후 75광장 정류장에 하차.&#xD;&#xD;&#xD;&#xD;</map><multifileId>MF00000192</multifileId><multifileIdx>25265</multifileIdx><name>75광장</name><parking>무</parking><phone></phone><product>/02164.web?gcode=1190&amp;idx=11247&amp;amode=view&amp;</product><sightseeing></sightseeing><source></source><trafficinfo></trafficinfo><usehour></usehour><xposition>35.07067170712426</xposition><yposition>129.05803058081557</yposition></item><item><address>부산광역시 영도구 영선동4가</address><assetage></assetage><assetdate></assetdate><assetnumber></assetnumber><assetscale></assetscale><category></category><content>영도구민들이 자주 찾는 해안산책로와 연결되어있는 패총벽화거리로 해안산책로까지 연결되는 거리이며 가족, 연인들끼리 해질녘에 걸으면 바다의 시원함을 느낄 수 있는 좋은 장소입니다. 걸으면서 알록달록한 조개모양 전등을 보면 아이들 또한 재미있게 산책 할 수 있을 것입니다.</content><copy></copy><course></course><etc></etc><fee>무료</fee><food></food><guide></guide><homepage></homepage><idx>2176</idx><institution></institution><islandName></islandName><manage></manage><map>&#xD;◾출발지: 영도대교 → 9, 85, 508, 71, 7번 영도대교에서 탑승 후 부산 보건고등학교에서 하차.&#xD;&#xD;◾출발지: 부산역 → 508, 85, 82번 탑승 후 부산 보건고등학교에서 하차.&#xD;&#xD;&#xD;</map><multifileId>MF00000332</multifileId><multifileIdx>25639</multifileIdx><name>패총벽화거리</name><parking>주차가능</parking><phone></phone><product></product><sightseeing></sightseeing><source></source><trafficinfo></trafficinfo><usehour>시간대와 관계없음 (연중무휴)</usehour><xposition>35.08238244090348</xposition><yposition>129.04070735941656</yposition></item><item><address>부산 영도구 청학동</address><assetage></assetage><assetdate></assetdate><assetnumber></assetnumber><assetscale></assetscale><category></category><content>영도구청에서 청학배수지의 공간을 전망대로 만들어 시민들에게 개방하였습니다. 전망대에서 바라보는 야경과 부산항대교의 불빛은 매니아들의 포토존으로 각광받고 있습니다. 또한 각종 운동기구가 설치 되어 있어 시원한 바람을 맞으며 산책, 조깅을 하기에 적합한 장소입니다. &#xD;&#xD;&#xD;&#xD;</content><copy></copy><course></course><etc></etc><fee>무료</fee><food></food><guide></guide><homepage></homepage><idx>2168</idx><institution></institution><islandName></islandName><manage></manage><map>&#xD;◾출발지: 영도대교 → 9번 탑승 후 (구)해사고에서 하차.&#xD;      &#xD;◾출발지: 부산역 → 지하철 1호선 남포역에서 하차 후 6번 출구로 나와 9번 탑승 하여 (구)해사고에서 하차.&#xD;&#xD;&#xD;&#xD;&#xD;</map><multifileId>MF00000316</multifileId><multifileIdx>25570</multifileIdx><name>청학배수지 전망대</name><parking></parking><phone></phone><product>/02164.web?gcode=1190&amp;idx=11242&amp;amode=view&amp;</product><sightseeing></sightseeing><source></source><trafficinfo></trafficinfo><usehour></usehour><xposition>35.08849684443571</xposition><yposition>129.06015590020405</yposition></item><item><address>부산시 영도구 해안산책길 52 (영선동4가) </address><assetage></assetage><assetdate></assetdate><assetnumber></assetnumber><assetscale></assetscale><category></category><content>영도 서쪽 편 봉래산 아래 해안선을 따라 이어져 있는 3Km의 해안산책로로써 원래 이 곳은 지형이 가파르고 험난하여 군사보호구역으로 접근이 어려웠으나 2001년 해안선을 따라 산책로가 개설되었습니다. 경치 좋은 절영해안 산책로는 곳곳에 장승과 돌탑, 뱃놀이터 등이 있어 볼거리들이 많으며 산책로 우측의 넓은 바다와 담벼락의 다양한 모자이크 타일 문양을 보고 있노라면 지루함을 잊은 채 거니실 수 있습니다. 2014년 국토해양부가 선정한 대한민국 5대 해안누리길로 선정되어 그 가치를 인정 받기도 하였습니다. 최근 2021 부산 안심관광지에 선정되어 관광지 방역 관리가 철저히 잘되어 있음을 입증하였습니다.&#xD;</content><copy></copy><course></course><etc></etc><fee></fee><food></food><guide></guide><homepage></homepage><idx>2160</idx><institution></institution><islandName></islandName><manage>영도구청</manage><map>◾출발지: 영도대교 → 9, 85, 508, 71, 7번 탑승 후 부산 보건고등학교에서 하차.&#xD;&#xD;◾출발지: 부산역 → 508, 85, 82번 탑승 후 부산 보건고등학교에서 하차.&#xD;&#xD;</map><multifileId>MF00000184</multifileId><multifileIdx>27308</multifileIdx><name>절영해안산책로</name><parking></parking><phone>051-419-4064</phone><product>/02164.web?gcode=1190&amp;idx=11236&amp;amode=view&amp;amode=view&amp;amp;cpage=2&amp;cpage=2&amp;amp;idx=11236</product><sightseeing></sightseeing><source></source><trafficinfo></trafficinfo><usehour>연중무휴</usehour><xposition>35.081144786</xposition><yposition>129.0412093165</yposition></item><item><address>부산 영도구 청학동 산 54-4</address><assetage></assetage><assetdate></assetdate><assetnumber></assetnumber><assetscale></assetscale><category></category><content>영도의 중앙에 위치하고 있는 봉래산(蓬萊山, 해발 395m)은 중국 전설에 나타나는 영산(靈山)인 삼신산(三神山) 가운데 하나입니다.&#xD;동쪽 바다의 가운데 있으며 신선이 살고, 불로초와 불사약이 있다고 하는 명산으로 중구, 서구, 해운대구 등의 부산의 시가지를 한눈에 볼수 있으며 산 위에서 내려다보는 일출과 일몰이 장관입니다. &#xD;또한 둘레길에 있는 꽃들과 나무들을 보며 자연의 싱그러움을 느끼며, 아름다운 경치 또한 구경하실 수 있습니다.&#xD;&#xD;&#xD;&#xD;&#xD;&#xD;&#xD;&#xD;&#xD;</content><copy></copy><course></course><etc></etc><fee>무료</fee><food></food><guide></guide><homepage></homepage><idx>2161</idx><institution></institution><islandName></islandName><manage></manage><map>◾출발지: 영도다리 → 6, 9번 탑승 후 신선동 주민센터 하차 후 약 600m 도보 이동/ 7, 71번 탑승 후 흰여울문화마을 하차 후 약 800m 도보 이동.&#xD;&#xD;◾출발지: 부산역 → 82, 85번 탑승 후 신선동 주민센터 하차 후 약 600m 도보 이동.&#xD;&#xD;&#xD;</map><multifileId>MF00000185</multifileId><multifileIdx>25242</multifileIdx><name>봉래산</name><parking></parking><phone>051-419-4064</phone><product>/02164.web?gcode=1190&amp;idx=11241&amp;amode=view&amp;</product><sightseeing></sightseeing><source></source><trafficinfo></trafficinfo><usehour></usehour><xposition>35.08220018986855</xposition><yposition>129.05522866493365</yposition></item><item><address>부산광역시 영도구 태종로 727 (동삼동) </address><assetage></assetage><assetdate></assetdate><assetnumber></assetnumber><assetscale></assetscale><category></category><content>부산 영도구 동삼(東三)동에 아침 섬, 한자로 표현하여 조도라고 불리며 영도 남단 1.8km지점에 위치하며 본래 절영도(오늘의 영도)의 ‘큰 섬에 대한 작은 섬’이란 뜻으로 아치섬이라 했다고 전해지고 있습니다. 이후 매립을 통해 점차 땅을 넓혔으며, 현재 해양대학교 캠퍼스가 자리잡고 있는 섬입니다.  &#xD;&#xD;&#xD;▣ 시설정보&#xD;&#xD;* 한국해양대학교: 5개 대학원(일반대학원, 해사산업대학원, 해양금융대학원, 글로벌물류대학원, 해양과학기술전문대학원), 4개 단과대학(해사대학, 해양과학기술대학, 공과대학, 국제대학)으로 구성되어 있다. 부설 연구기관으로 해사산업연구소, 산업기술연구소, 해양과학기술연구소, 국제해양문제연구소 등이 있다. 해운계의 고급인력 양성과 해운·해양 관련 과학의 연구를 교육목표로 삼고 있습니다.&#xD;&#xD;&#xD;&#xD;</content><copy></copy><course></course><etc></etc><fee></fee><food></food><guide></guide><homepage></homepage><idx>2162</idx><institution></institution><islandName></islandName><manage></manage><map>◾출발지: 영도대교 → 190, 30, 101, 88A, 8번 탑승 후 해양대학교 입구 정류장에 하차.&#xD;&#xD;◾출발지: 부산역 → 190번 탑승 후 해양대승선생활관 정류장에 하차.&#xD;&#xD;&#xD;</map><multifileId>MF00000190</multifileId><multifileIdx>25247</multifileIdx><name>조도(아치섬)</name><parking></parking><phone>051-410-4114</phone><product>/02164.web?gcode=1190&amp;idx=11238&amp;amode=view&amp;</product><sightseeing></sightseeing><source></source><trafficinfo></trafficinfo><usehour></usehour><xposition>35.0744077694</xposition><yposition>129.0873485791</yposition></item><item><address>부산광역시 영도구 태종로 729 (동삼동) </address><assetage></assetage><assetdate>1979년 7월 26일</assetdate><assetnumber>사적 제266호</assetnumber><assetscale></assetscale><category></category><content>동삼동패총은 여러 차례의 발굴조사로 빗살무늬토기를 비롯하여 각종 석기, 뼈연모, 토제품, 장신구와 함께 다양한 어패류와 동물뼈가 출토되었습니다. 또한 한·일 신석기문화의 교류관계를 알려주는 많은 양의 죠몽토기와 흑요석 등이 출토되어 우리나라 신석기 문화의 성격과 실체를 규명하는 중요한 유적으로써 동삼동패총 유적지와 발굴유물을 국내외에 공개하고, 살아있는 역사교육의 장으로 활용하기 위해 동삼패총전시관을 2002년 개관하였습니다. 현재 신석기 시대의 역사 문화 연구의 구심점이 될 동삼동 패총전시관에는 현재 빗살무늬 토기 및 석기를 비롯 100여점의 유물이 전시 중에 있습니다.&#xD;&#xD;&#xD;&#xD;자세한 정보 및 전시해설 신청은 http://museum.busan.go.kr/dongsam로 들어가시면 확인 하실 수 있습니다. (동삼동패총 전시관: 051-403-1193)&#xD;&#xD;&#xD;&#xD;&#xD;</content><copy></copy><course></course><etc></etc><fee></fee><food></food><guide></guide><homepage>http://museum.busan.go.kr/dongsam</homepage><idx>2163</idx><institution></institution><islandName></islandName><manage></manage><map>◾출발지: 영도대교 → 30, 88A, 90, 190, 101번 탑승 후 해양대입구 정류장에 하차.&#xD;&#xD;◾출발지: 부산역 → 101번 탑승 후 해양대 입구 정류장에 하차.&#xD;&#xD;&#xD;&#xD;</map><multifileId>MF00000191</multifileId><multifileIdx>27327</multifileIdx><name>동삼동 패총전시관</name><parking>4대 가능</parking><phone>051-403-1193</phone><product>/02164.web?gcode=1190&amp;idx=11243&amp;amode=view&amp;</product><sightseeing></sightseeing><source></source><trafficinfo></trafficinfo><usehour>09:00 ~ 18:00 / 휴무 : 1월1일, 매주 월요일 (공휴일인 경우 다음날 휴관)&#xD;* 코로나19 확산 방지를 위해 2020. 9. 27.(일)까지 임시휴관</usehour><xposition>35.0712162442</xposition><yposition>129.0796688712</yposition></item></items><numOfRows>10</numOfRows><pageNo>1</pageNo><totalCount>145</totalCount></body></response>
        결과:null
        ```
        
    
- json → object x
    
    > 코드
    > 
    
    ```java
    위의 코드 x 
    return type을 StringBuild로. 
    ```
    
    > 에러
    > 
    - 에러내용
        
        ```java
        8월 02, 2022 3:46:11 오후 org.apache.catalina.core.ApplicationDispatcher invoke
        심각: 서블릿 [jsp]을(를) 위한 Servlet.service() 호출이 예외를 발생시켰습니다.
        javax.servlet.jsp.JspTagException: Don't know how to iterate over supplied "items" in &lt;forEach&gt;
        	at org.apache.taglibs.standard.tag.common.core.ForEachSupport.toForEachIterator(ForEachSupport.java:274)
        	at org.apache.taglibs.standard.tag.common.core.ForEachSupport.supportedTypeForEachIterator(ForEachSupport.java:238)
        	at org.apache.taglibs.standard.tag.common.core.ForEachSupport.prepare(ForEachSupport.java:155)
        	at javax.servlet.jsp.jstl.core.LoopTagSupport.doStartTag(LoopTagSupport.java:256)
        	at org.apache.jsp.WEB_002dINF.views.result.busanYDs_jsp._jspx_meth_c_005fforEach_005f0(busanYDs_jsp.java:179)
        	at org.apache.jsp.WEB_002dINF.views.result.busanYDs_jsp._jspService(busanYDs_jsp.java:139)
        	at org.apache.jasper.runtime.HttpJspBase.service(HttpJspBase.java:70)
        	at javax.servlet.http.HttpServlet.service(HttpServlet.java:764)
        	at org.apache.jasper.servlet.JspServletWrapper.service(JspServletWrapper.java:466)
        	at org.apache.jasper.servlet.JspServlet.serviceJspFile(JspServlet.java:379)
        	at org.apache.jasper.servlet.JspServlet.service(JspServlet.java:327)
        	at javax.servlet.http.HttpServlet.service(HttpServlet.java:764)
        	at org.apache.catalina.core.ApplicationFilterChain.internalDoFilter(ApplicationFilterChain.java:227)
        	at org.apache.catalina.core.ApplicationFilterChain.doFilter(ApplicationFilterChain.java:162)
        	at org.apache.tomcat.websocket.server.WsFilter.doFilter(WsFilter.java:53)
        	at org.apache.catalina.core.ApplicationFilterChain.internalDoFilter(ApplicationFilterChain.java:189)
        	at org.apache.catalina.core.ApplicationFilterChain.doFilter(ApplicationFilterChain.java:162)
        	at org.apache.catalina.core.ApplicationDispatcher.invoke(ApplicationDispatcher.java:711)
        	at org.apache.catalina.core.ApplicationDispatcher.processRequest(ApplicationDispatcher.java:459)
        	at org.apache.catalina.core.ApplicationDispatcher.doForward(ApplicationDispatcher.java:385)
        	at org.apache.catalina.core.ApplicationDispatcher.forward(ApplicationDispatcher.java:313)
        	at org.springframework.web.servlet.view.InternalResourceView.renderMergedOutputModel(InternalResourceView.java:168)
        	at org.springframework.web.servlet.view.AbstractView.render(AbstractView.java:303)
        	at org.springframework.web.servlet.DispatcherServlet.render(DispatcherServlet.java:1257)
        	at org.springframework.web.servlet.DispatcherServlet.processDispatchResult(DispatcherServlet.java:1037)
        	at org.springframework.web.servlet.DispatcherServlet.doDispatch(DispatcherServlet.java:980)
        	at org.springframework.web.servlet.DispatcherServlet.doService(DispatcherServlet.java:897)
        	at org.springframework.web.servlet.FrameworkServlet.processRequest(FrameworkServlet.java:970)
        	at org.springframework.web.servlet.FrameworkServlet.doPost(FrameworkServlet.java:872)
        	at javax.servlet.http.HttpServlet.service(HttpServlet.java:681)
        	at org.springframework.web.servlet.FrameworkServlet.service(FrameworkServlet.java:846)
        	at javax.servlet.http.HttpServlet.service(HttpServlet.java:764)
        	at org.apache.catalina.core.ApplicationFilterChain.internalDoFilter(ApplicationFilterChain.java:227)
        	at org.apache.catalina.core.ApplicationFilterChain.doFilter(ApplicationFilterChain.java:162)
        	at org.apache.tomcat.websocket.server.WsFilter.doFilter(WsFilter.java:53)
        	at org.apache.catalina.core.ApplicationFilterChain.internalDoFilter(ApplicationFilterChain.java:189)
        	at org.apache.catalina.core.ApplicationFilterChain.doFilter(ApplicationFilterChain.java:162)
        	at org.springframework.web.filter.CharacterEncodingFilter.doFilterInternal(CharacterEncodingFilter.java:197)
        	at org.springframework.web.filter.OncePerRequestFilter.doFilter(OncePerRequestFilter.java:107)
        	at org.apache.catalina.core.ApplicationFilterChain.internalDoFilter(ApplicationFilterChain.java:189)
        	at org.apache.catalina.core.ApplicationFilterChain.doFilter(ApplicationFilterChain.java:162)
        	at com.navercorp.lucy.security.xss.servletfilter.XssEscapeServletFilter.doFilter(XssEscapeServletFilter.java:36)
        	at org.apache.catalina.core.ApplicationFilterChain.internalDoFilter(ApplicationFilterChain.java:189)
        	at org.apache.catalina.core.ApplicationFilterChain.doFilter(ApplicationFilterChain.java:162)
        	at org.apache.catalina.core.StandardWrapperValve.invoke(StandardWrapperValve.java:197)
        	at org.apache.catalina.core.StandardContextValve.invoke(StandardContextValve.java:97)
        	at org.apache.catalina.authenticator.AuthenticatorBase.invoke(AuthenticatorBase.java:541)
        	at org.apache.catalina.core.StandardHostValve.invoke(StandardHostValve.java:135)
        	at org.apache.catalina.valves.ErrorReportValve.invoke(ErrorReportValve.java:92)
        	at org.apache.catalina.valves.AbstractAccessLogValve.invoke(AbstractAccessLogValve.java:687)
        	at org.apache.catalina.core.StandardEngineValve.invoke(StandardEngineValve.java:78)
        	at org.apache.catalina.connector.CoyoteAdapter.service(CoyoteAdapter.java:360)
        	at org.apache.coyote.http11.Http11Processor.service(Http11Processor.java:399)
        	at org.apache.coyote.AbstractProcessorLight.process(AbstractProcessorLight.java:65)
        	at org.apache.coyote.AbstractProtocol$ConnectionHandler.process(AbstractProtocol.java:890)
        	at org.apache.tomcat.util.net.NioEndpoint$SocketProcessor.doRun(NioEndpoint.java:1787)
        	at org.apache.tomcat.util.net.SocketProcessorBase.run(SocketProcessorBase.java:49)
        	at org.apache.tomcat.util.threads.ThreadPoolExecutor.runWorker(ThreadPoolExecutor.java:1191)
        	at org.apache.tomcat.util.threads.ThreadPoolExecutor$Worker.run(ThreadPoolExecutor.java:659)
        	at org.apache.tomcat.util.threads.TaskThread$WrappingRunnable.run(TaskThread.java:61)
        	at java.lang.Thread.run(Thread.java:748)
        ```
        

openapi2.html처럼 만들어보기. → 처음부터 다시 해야함.