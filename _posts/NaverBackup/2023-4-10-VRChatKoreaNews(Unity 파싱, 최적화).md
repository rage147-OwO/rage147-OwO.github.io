---
title: "VRChatKoreaNews(Unity 파싱, 최적화)"
categories:
 - personalproject
---
#VRChatKoreaNews(Unity 파싱, 최적화) : 네이버 블로그
<div class="wrap_rabbit pcol2 _param(1) _postViewArea223070750906" id="post-view223070750906">
<!-- Rabbit HTML --><div class="se-viewer se-theme-default" lang="ko-KR">
<!-- SE_DOC_HEADER_END -->
<div class="se-main-container">
<div class="se-component se-text se-l-default" id="SE-772b0179-9d42-4647-937e-2a5e1ba38d05">
<div class="se-component-content">
<div class="se-section se-section-text se-l-default">
<div class="se-module se-module-text">
<!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-971f328f-49b9-45f8-9899-e3a1d939f18f" style=""><span class="se-fs- se-ff-" id="SE-48c90cd2-4416-4743-ad93-3bf1bd1cafe2" style="">저번 포스팅에서 구글 클라우드 컴퓨팅으로 github에 자동으로 뉴스가 커밋되게 해놓았으니, 유니티에서 받아야 한다.</span></p><!-- } SE-TEXT --><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-c7f845a6-689e-4e5b-97f8-f684e67f3beb" style=""><span class="se-fs- se-ff-" id="SE-1efa8657-8c82-4863-894b-5cfcd45c95fa" style="">​</span></p><!-- } SE-TEXT --><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-aeeb5722-4c21-4493-afa5-c81e88a811e3" style=""><span class="se-fs- se-ff-" id="SE-72d31ef0-a112-4792-8ab6-adbcda1cef5a" style=""><a class="se-link" href="https://youtu.be/Ku52Hjhq1mA" target="_blank">https://youtu.be/Ku52Hjhq1mA</a></span></p><!-- } SE-TEXT -->
</div>
</div>
</div>
</div> <div class="se-component se-oembed se-l-default" id="SE-b9eae2b9-c0cc-46d0-820e-cfe2518a1254">
<div class="se-component-content se-component-content-fit">
<div class="se-section se-section-oembed se-section-align- se-l-default">
<div class="se-module se-module-oembed se-is-progress" style="padding-top: 56.25%;"></div>
</div>
</div>
<script class="__se_module_data" data-module='{"type":"v2_oembed", "id" :"SE-b9eae2b9-c0cc-46d0-820e-cfe2518a1254", "data" : { "html": "&lt;iframe width=\"400\" height=\"225\" src=\"https://www.youtube.com/embed/Ku52Hjhq1mA?feature=oembed\" frameborder=\"0\" allow=\"accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share\" allowfullscreen title=\"VRChatKoreaNews\"&gt;&lt;/iframe&gt;", "originalWidth" : "400", "originalHeight" : "225", "contentMode" : "fit", "description": "VRChatKoreaNewshttps://rage147.booth.pm/items/4681116How To Makehttps://blog.naver.com/dls32208/223070716515", "inputUrl": "https://youtu.be/Ku52Hjhq1mA", "thumbnailUrl" : "https://i.ytimg.com/vi/Ku52Hjhq1mA/hqdefault.jpg", "thumbnailHeight" : "360", "thumbnailWidth" : "480", "title": "VRChatKoreaNews", "providerUrl": "https://www.youtube.com/", "align": "", "type" : "video" }}' type="text/data"></script>
</div>
<div class="se-component se-text se-l-default" id="SE-a565f824-3567-4ac3-b01f-fa61d782d95a">
<div class="se-component-content">
<div class="se-section se-section-text se-l-default">
<div class="se-module se-module-text">
<!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-9d1adff7-4909-4cbd-a61b-dd3f7a11889b" style=""><span class="se-fs- se-ff-" id="SE-6ba7d445-0dc3-4f8d-ab0a-f177adb591f3" style="">우선 시연 영상이다.</span></p><!-- } SE-TEXT --><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-5480cddc-27f2-45e4-8066-77b461794c0a" style=""><span class="se-fs- se-ff-" id="SE-7963f479-ccdb-49e1-a3ae-58d40e3ddecb" style="">​</span></p><!-- } SE-TEXT --><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-73d791b8-60df-4ddb-abaf-80369297fffd" style=""><span class="se-fs- se-ff-" id="SE-1ac49c32-2f96-4370-b100-46564440a24d" style="">스크롤뷰와 버튼을 이용하여 만들었다.</span></p><!-- } SE-TEXT --><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-371e8980-3356-47ae-a314-72235d5c487b" style=""><span class="se-fs- se-ff-" id="SE-09919230-d646-42d4-8be5-0fd538353384" style="">​</span></p><!-- } SE-TEXT --><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-05cbc0f8-9eca-4092-b681-88d11a1565e6" style=""><span class="se-fs- se-ff-" id="SE-931ac12e-9650-4872-8918-ef97d1ab291e" style="">UGui의 든든 국밥같은 친구, 스크롤뷰의 LayoutGroup과 ContentSizeFilter를 이용했다.</span></p><!-- } SE-TEXT --><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-7630accb-b0a9-4030-bb9e-1d059b6bf9dd" style=""><span class="se-fs- se-ff-" id="SE-0f1376c4-6ac9-4329-81af-af384362a95f" style="">​</span></p><!-- } SE-TEXT --><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-2f35501f-50f4-443d-ba21-ecc99d826f16" style=""><span class="se-fs- se-ff-" id="SE-5caa550a-6ca0-42b0-a0a4-3fc52606b654" style="">LayoutGroup은 자식 오브젝트를 자동으로 정렬해주는 기능이다. 수직 또는 수평으로 자식 오브젝트를 나열하고, 간격을 설정할 수 있다. </span></p><!-- } SE-TEXT --><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-58ea19cd-9326-44a7-bd6c-a6e7030f1f21" style=""><span class="se-fs- se-ff-" id="SE-5bd8e097-4299-403c-88fa-7c89d355b85b" style="">​</span></p><!-- } SE-TEXT --><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-11538408-0706-4fa3-a9d8-c21ff8829b9a" style=""><span class="se-fs- se-ff-" id="SE-cb45515d-ebbd-4a63-89c2-909840a67326" style="">ContentSizeFilter는 UI 요소의 크기를 자동으로 조절하는 기능이다. 이 컴포넌트를 사용하면 부모 오브젝트의 크기에 맞게 UI 요소의 크기를 조절할 수 있다. 예를 들면, 부모 오브젝트의 크기가 변경되면 자식 UI 요소의 크기도 자동으로 조절된다.</span></p><!-- } SE-TEXT --><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-642a3a71-9593-4d79-b119-318b6a21ad54" style=""><span class="se-fs- se-ff-" id="SE-fd4b44ff-ba25-4fa6-9233-fdc57ea90e62" style="">​</span></p><!-- } SE-TEXT --><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-fbf775bc-3ba6-4b09-9a6b-d32862295277" style=""><span class="se-fs- se-ff-" id="SE-38c991f0-342a-4215-a37e-65bf1a3faf49" style="">​</span></p><!-- } SE-TEXT --><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-50f0d838-91d6-48b4-a4e8-031c848f1910" style=""><span class="se-fs- se-ff-" id="SE-b4c0f2ed-9f25-4302-a372-7d9c9035e1e3" style="">​</span></p><!-- } SE-TEXT --><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-62671021-3103-471b-a127-d0e6e0649388" style=""><span class="se-fs- se-ff-" id="SE-10b4ef07-6d2d-482e-93dc-ebe19b0fe2f3" style="">원래는 버튼을 생성하는쪽으로 생각했으나, 언론사를 바꿀때마다 생성과 삭제가 반복되니, Setactive하는게 조금 더 나을거라고 생각해서 20개를 생성 해둔 뒤 끄는 방향으로 하였다.</span></p><!-- } SE-TEXT --><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-dd198604-d7da-49a4-90c0-1b83b0e9b5ec" style=""><span class="se-fs- se-ff-" id="SE-efa1144c-335f-47e8-a47c-8c8e6c3849cd" style="">​</span></p><!-- } SE-TEXT --><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-af233179-b240-4122-98fe-c4227059ed9d" style=""><span class="se-fs- se-ff-" id="SE-d00890c3-081b-41be-a38c-5419c945ac3b" style="">스크롤뷰 하위에 버튼을 넣으면 레이캐스트가 겹쳐, 버튼의 클릭이 되지 않고 스크롤뷰로 가는 버그가 있는데, Event Trigger컴포넌트를 넣어 우선 순위를 올려주면 된다. </span></p><!-- } SE-TEXT --><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-00141fa5-a114-4a68-b691-e83181c0cd38" style=""><span class="se-fs- se-ff-" id="SE-b168d577-cc2d-4e0f-a35a-8647425ee72e" style="">​</span></p><!-- } SE-TEXT --><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-ee27068b-6ddd-4c42-8ba2-4c807ddf693f" style=""><span class="se-fs- se-ff-" id="SE-57cf3c1a-420e-4d87-84b1-a20e75b66586" style="">그 밖에는... 음..</span></p><!-- } SE-TEXT --><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-ed9a1592-d3af-45aa-9601-21411a0bb29f" style=""><span class="se-fs- se-ff-" id="SE-45a5cf79-0c96-4ac2-9a33-2819212b840f" style="">​</span></p><!-- } SE-TEXT --><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-ad90be51-7452-41e5-a3f4-fd61fb8102c2" style=""><span class="se-fs- se-ff-" id="SE-05e0535b-7a00-4ab4-aac9-cb043d38f347" style="">글자 해상도를 올리려면 폰트를 키우고 오브젝트 사이즈를 줄이면 된다?</span></p><!-- } SE-TEXT --><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-a245e3ba-d5b3-4599-9400-3f54d14e72ac" style=""><span class="se-fs- se-ff-" id="SE-c0315d98-8992-4256-8282-cc9ce047ac2b" style="">​</span></p><!-- } SE-TEXT --><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-fb1800ce-1850-4a0d-ad8e-1e2f54c3d6bf" style=""><span class="se-fs- se-ff-" id="SE-25566a30-a3b7-4e00-8424-0bb98e30c349" style="">VRChat한정으로 버튼과 상호작용을 하려면 레이아웃을 디폴트로, 캔버스에 VRC UI Shape 컴포넌트를 넣어줘야 한다.</span></p><!-- } SE-TEXT --><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-ed74f04f-589d-49e8-95ac-6d7824a1ba6a" style=""><span class="se-fs- se-ff-" id="SE-2659855b-6cfa-4ffd-8bb9-0a4b4ac8a4c9" style="">​</span></p><!-- } SE-TEXT --><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-acd0935c-c143-470c-90c3-f4d6f1c25b71" style=""><span class="se-fs- se-ff-" id="SE-96645c17-e6d4-456d-81e0-6e2b8fadd36d" style="">그 밖에는 WASD키를 누르면 UI가 움직이니 Navigation을 꺼야 한다 정도?</span></p><!-- } SE-TEXT --><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-5353ec52-3515-4b2c-87b8-2d30893824df" style=""><span class="se-fs- se-ff-" id="SE-d2663ec5-5b00-4104-943e-b0f8e6aba368" style="">​</span></p><!-- } SE-TEXT --><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-71ba3623-3663-4da3-85df-fbd488b5a00a" style=""><span class="se-fs- se-ff-" id="SE-ccc09c40-2b43-4e73-be17-4e2b791a8579" style="">사실 구현보다 배경 텍스쳐 고르는게 더 힘들었다 ㅋㅋ</span></p><!-- } SE-TEXT --><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-39e7dd14-5fa7-46ef-b2b2-b24743b0d4e7" style=""><span class="se-fs- se-ff-" id="SE-43322847-0fff-4167-8b82-8671a7cd9c1e" style="">​</span></p><!-- } SE-TEXT --><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-1a06caf9-6310-4b41-9bd8-8992b5ee7bd9" style=""><span class="se-fs- se-ff-" id="SE-d1a660f9-fe6f-40ff-bbf9-541be990cf79" style="">이과의 감성이란..</span></p><!-- } SE-TEXT --><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-5cc6b8fc-edd2-4bac-9b2b-604c76fcc9b3" style=""><span class="se-fs- se-ff-" id="SE-e05b4e3f-435f-40d7-9a87-a0eb1c71a746" style="">​</span></p><!-- } SE-TEXT --><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-6b869b94-bfc5-4327-a7cd-74200160d5d4" style=""><span class="se-fs- se-ff-" id="SE-a99c41f1-c754-4da3-85ba-dfcc3dfd0bfd" style="">===================================</span></p><!-- } SE-TEXT --><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-9f5d78d5-2d0d-4694-acfb-0a618cac8ffa" style=""><span class="se-fs- se-ff-" id="SE-4786d2c5-6695-410f-8dd7-97a2a7b1a703" style="">​</span></p><!-- } SE-TEXT --><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-b0ee9ee9-3354-4d9f-9bbc-8163be7e8d51" style=""><span class="se-fs- se-ff-" id="SE-1348e73a-2d70-4191-9f7f-96c5bb6f9be1" style="">스크립트는 두개가 들어가는데</span></p><!-- } SE-TEXT --><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-6d0d61e5-ee3d-4372-b780-71f160278a07" style=""><span class="se-fs- se-ff-" id="SE-57a960f4-b705-4aff-bf7f-f5f61adb4ec3" style="">하나는 메인 KoreaNews이고 하나는 KoreaNewsButton이다.</span></p><!-- } SE-TEXT --><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-cee22afd-4774-4376-b67a-1b510421d12d" style=""><span class="se-fs- se-ff-" id="SE-2c283dbc-2cd7-4504-99fb-ab8ea94d94c9" style="">VRChat에서는 버튼을 누를 때 매개변수를 전달 할 수 없기에, 본인에게 보낸 뒤 코드에서 처리해야지, 버튼이 어디에서 눌린 것인지 알 수 있다.</span></p><!-- } SE-TEXT --><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-a8f2add7-6814-49a2-91a8-725ec6b1f1a7" style=""><span class="se-fs- se-ff-" id="SE-ebb5f13f-9720-408e-b1fe-f3eddda1ca7e" style="">​</span></p><!-- } SE-TEXT --><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-0e375c0f-46af-42e1-aa94-580b5cdb1695" style=""><span class="se-fs- se-ff-" id="SE-c8090588-66ce-42e0-8046-01b159bfeb90" style="">아래는 버튼의 코드이다.</span></p><!-- } SE-TEXT -->
</div>
</div>
</div>
</div> <div class="se-component se-code se-l-code_black" id="SE-74f6476d-9ea8-4358-a9a4-61dd3a161b97">
<div class="se-component-content">
<div class="se-section se-section-code se-l-code_black">
<div class="se-module se-module-code se-fs-fs13">
<div class="se-code-source">
<div class="__se_code_view language-javascript">    public void ButtonClicked()
    {
        transform.parent.parent.parent.parent.GetComponent&lt;UdonBehaviour&gt;()
            .SendCustomEvent(name.Substring(0,5)+transform.GetSiblingIndex());
        
    }</div>
</div>
</div>
</div>
</div>
<script class="__se_module_data" data-module='{"type":"v2_code", "id" : "SE-74f6476d-9ea8-4358-a9a4-61dd3a161b97"}' type="text/data"></script>
</div> <div class="se-component se-text se-l-default" id="SE-aa946467-fc96-4f3e-9583-dd7e7ac0805d">
<div class="se-component-content">
<div class="se-section se-section-text se-l-default">
<div class="se-module se-module-text">
<!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-f28e36af-d036-46ff-a181-ea642458e73c" style=""><span class="se-fs- se-ff-" id="SE-9cc6c9df-ff4e-47bf-ae35-e91d6e4275ef" style="">버튼의 상위 UdonBehavior를 찾은 뒤 자신의 이름 앞 5글자와 본인의 하이라키 순서를 이벤트 이름으로 보낸다.</span></p><!-- } SE-TEXT --><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-9cfe35a6-10b7-4539-887c-faf147e7e3a5" style=""><span class="se-fs- se-ff-" id="SE-497efbce-ad70-4f9a-9496-1099dadbd7d8" style="">transfor</span><span class="se-fs- se-ff-" id="SE-607fac12-9d8e-4be3-bcb1-e8e8438cc3b2" style=""><a class="se-link" href="http://m.parent.parent.parent.parent" target="_blank">m.parent.parent.parent.parent</a></span><span class="se-fs- se-ff-" id="SE-dfb177e8-856c-4ed2-ab9c-8fbce515775c" style="">는 추하긴 하지만... GetComponentInParent보다는 낫지 않을까? 싶다.</span></p><!-- } SE-TEXT --><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-81a0ba3c-f311-46fb-94d2-999a68434b00" style=""><span class="se-fs- se-ff-" id="SE-160a4dbe-0276-424f-9112-59e5ee556b12" style="">​</span></p><!-- } SE-TEXT --><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-792c9c13-cc00-4fca-a561-31f50e5eeb28" style=""><span class="se-fs- se-ff-" id="SE-82dc0a0e-2350-4391-91e8-019f65f11f77" style="">아. 몰랐었는데 GetComponentInParent는 본인부터 찾기 때문에 transform.parent를 하고 GetComponentInParent을 사용해야 한다.</span></p><!-- } SE-TEXT --><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-03834717-c02a-4d8b-969e-b47dbd995886" style=""><span class="se-fs- se-ff-" id="SE-e0e6d1da-6331-4f8f-a46d-3fe3946b17ac" style="">​</span></p><!-- } SE-TEXT --><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-67b7401f-d01b-4b6b-a926-1e54003a23b9" style=""><span class="se-fs- se-ff-" id="SE-3350e2ff-6412-4a39-8223-623a340ec618" style="">나중에 작동이 안된다면 필시 여기 부분 일 것이다.</span></p><!-- } SE-TEXT --><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-5abe8b87-2e9f-40df-8755-f2adf9cdb1b0" style=""><span class="se-fs- se-ff-" id="SE-92beb620-720e-4f45-9c3f-2d8ee424256b" style="">​</span></p><!-- } SE-TEXT -->
</div>
</div>
</div>
</div> <div class="se-component se-code se-l-code_black" id="SE-1dc5583d-2b41-4ea7-ab04-e3122e3f0ace">
<div class="se-component-content">
<div class="se-section se-section-code se-l-code_black">
<div class="se-module se-module-code se-fs-fs13">
<div class="se-code-source">
<div class="__se_code_view language-javascript">using System;
using System.Linq;
using System.Text;
using UdonSharp;
using UnityEngine;
using UnityEngine.UI;
using VRC.SDK3.StringLoading;
using VRC.SDKBase;
using VRC.Udon;

public class KoreaNews : UdonSharpBehaviour
{
    private VRCUrl[] pressUrls = new VRCUrl[]
    {
        new VRCUrl("https://rage147-owo.github.io/VRChatKoreaNews/%EB%8F%99%EC%95%84%EC%9D%BC%EB%B3%B4.html"),
        new VRCUrl("https://rage147-owo.github.io/VRChatKoreaNews/%EB%A7%A4%EC%9D%BC%EA%B2%BD%EC%A0%9C.html"),
        new VRCUrl("https://rage147-owo.github.io/VRChatKoreaNews/%EC%A1%B0%EC%84%A0%EC%9D%BC%EB%B3%B4.html")
    };

    private string[] pressNames = new string[]
    {
        "동아일보",
        "매일경제",
        "조선일보"
    };
    [SerializeField] private Transform pressButtonParent;
    [SerializeField] private Transform themaButtonParent;
    [SerializeField] private Text newsText;
    [SerializeField] private Text PickUpText;
    [SerializeField] private int pageSize = 4;
    [SerializeField] private Text pageText;
    [SerializeField] private Text StatusText;

    private string _news;
    private string _articles;
    private string[] _thema;
    private int _currentPage = 1;
    private int _currentThema = 0;
    private int _maxPage;
    private int[] _themaIndexes;
    private int[] _pageIndexes;
    bool IsReady = false;

    private void Start()
    {
        Debug.Log("pressNameLength" + pressNames.Length);
        CreateButtons(pressButtonParent, pressNames.Length, pressNames);
        themaButtonParent.gameObject.SetActive(false);
        SetStatusText("IsReady");
    }

    private void SetStatusText(string __text)
    {
        StatusText.text = __text;
    }

    public override void OnStringLoadSuccess(IVRCStringDownload result)
    {
        _news = result.Result.Substring(49, result.Result.Length - 16 - 49);
        int firstNewlineIndex = _news.IndexOf('\n');
        _thema = _news.Substring(0, firstNewlineIndex).TrimEnd('_').Split('_');
        _news = _news.Remove(0, firstNewlineIndex + 1);
        CreateButtons(themaButtonParent, _thema.Length, _thema);
        SetThemaIndexes();
        SetStatusText("Last Update: " + DateTime.Now.ToString("yyyy-MM-dd HH:mm:ss"));
        themaButtonParent.gameObject.SetActive(true);
    }

    private void CreateButtons(Transform parent, int buttonCount, string[] buttonTexts)
    {
        Debug.Log("CreateButtons: " + buttonCount + " called");

        Text[] textComponents = parent.GetComponentsInChildren&lt;Text&gt;();

        for (int i = 0; i &lt; textComponents.Length; i++)
        {
            if (i &lt; buttonCount)
            {
                textComponents[i].transform.parent.gameObject.SetActive(true);
                textComponents[i].text = buttonTexts[i];
            }
            else
            {
                textComponents[i].transform.parent.gameObject.SetActive(false);
            }
        }
    }

    private void ShowPage(int page, int themeIndex)
    {

        pageText.text = page + "/" + _maxPage;
        if (page == 1)
        {
            newsText.text = _articles.Substring(0, _pageIndexes[1]);
            PickUpText.text = newsText.text;
        }
        else if (page == _maxPage)
        {
            Debug.Log("LastPage");
            newsText.text = _articles.Substring(_pageIndexes[_pageIndexes.Length-1], _articles.Length - _pageIndexes[_pageIndexes.Length - 1]);
            PickUpText.text = newsText.text;
        }
        else
        {
            newsText.text = _articles.Substring(_pageIndexes[page - 1], _pageIndexes[page] - _pageIndexes[page - 1]);
            PickUpText.text = newsText.text;
        }
    }

    private string GetArticlesForTheme(int themeIndex)
    {
        if (themeIndex == 0)
        {
            return _news.Substring(0, _themaIndexes[0]);
        }

        if (themeIndex == _thema.Length - 1)
        {
            return _news.Substring(_themaIndexes[themeIndex - 1], _news.Length - _themaIndexes[themeIndex - 1]);
        }

        return _news.Substring(_themaIndexes[themeIndex - 1],
            _themaIndexes[themeIndex] - _themaIndexes[themeIndex - 1]);
    }
    
    public void NextPage()
    {
        if(IsReady== false)
            return;
        Debug.Log("NextPage");
        if (_currentPage &lt; _maxPage)
        {
            _currentPage++;
            ShowPage(_currentPage, _currentThema);
        }
    }

    public void PrePage()
    {
        if(IsReady== false)
            return;
        Debug.Log("PrePage");
        if (_currentPage &gt; 1)
        {
            _currentPage--;
            ShowPage(_currentPage, _currentThema);
        }
    }

</div>
</div>
</div>
</div>
</div>
<script class="__se_module_data" data-module='{"type":"v2_code", "id" : "SE-1dc5583d-2b41-4ea7-ab04-e3122e3f0ace"}' type="text/data"></script>
</div> <div class="se-component se-code se-l-code_black" id="SE-d353cfee-f9c7-416e-9cda-e1bf11561255">
<div class="se-component-content">
<div class="se-section se-section-code se-l-code_black">
<div class="se-module se-module-code se-fs-fs13">
<div class="se-code-source">
<div class="__se_code_view language-javascript">private void SetPageIndexes(int themeIndex)
    {
        _articles = GetArticlesForTheme(themeIndex);
        int count = 0;
        for (int i = 0; i &lt; _articles.Length; i++)
        {
            if (_articles[i] == '_')
            {
                Debug.Log(_articles);
                count++;
            }
        }
        _maxPage = count / pageSize;

        if (count &lt; pageSize*2)
        {
            _maxPage = 2;
        }
        _pageIndexes = new int[_maxPage];

        int lastIndex = 0;
        int temp = 0;
        
        
        for (int i = 0; i &lt; count; i++)
        {
            if(_pageIndexes.Length == temp)
            {
                Debug.Log(temp);
                for(int j=0;j&lt;_pageIndexes.Length;j++)
                {
                    Debug.Log("PageIndexes: " + j + " " + _pageIndexes[j]);
                }
                break;
            }
            int currentIndex = _articles.IndexOf('_', lastIndex);
            lastIndex = currentIndex + 1;

            if (i % pageSize == 0)
            {
                _pageIndexes[temp] = currentIndex;
                temp++;
            }
        }
        IsReady= true;
    }

    private void SetThemaIndexes()
    {
        int themeCount = _thema.Length;
        _themaIndexes = new int[themeCount - 1];

        int lastIndex = 0;

        for (int i = 0; i &lt; themeCount - 1; i++)
        {
            int currentIndex = _news.IndexOf('^', lastIndex);
            _themaIndexes[i] = currentIndex;
            lastIndex = currentIndex + 1;
        }
    }

    public void ThemaButtonClicked(int themaIndex)
    {
        Debug.Log("ThemaButtonCkick : " + themaIndex + "");
        _currentThema = themaIndex;
        SetPageIndexes(themaIndex);
        _currentPage = 1; // reset the current page to 1 when changing themes
        ShowPage(1, themaIndex);
    }

    public void Press(int pressIndex)
    {
        Debug.Log("PressButton : " + pressIndex + "");

        VRC.SDK3.StringLoading.VRCStringDownloader.LoadUrl(pressUrls[pressIndex], GetComponent&lt;UdonBehaviour&gt;());
        themaButtonParent.gameObject.SetActive(false);
        SetStatusText("Loading...");
    }

    public void Thema0()
    {
        ThemaButtonClicked(0);
    }

    public void Thema1() =&gt; ThemaButtonClicked(1);
    public void Thema2() =&gt; ThemaButtonClicked(2);
    public void Thema3() =&gt; ThemaButtonClicked(3);
    public void Thema4() =&gt; ThemaButtonClicked(4);
    public void Thema5() =&gt; ThemaButtonClicked(5);
    public void Thema6() =&gt; ThemaButtonClicked(6);
    public void Thema7() =&gt; ThemaButtonClicked(7);
    public void Thema8() =&gt; ThemaButtonClicked(8);
    public void Thema9() =&gt; ThemaButtonClicked(9);
    public void Thema10() =&gt; ThemaButtonClicked(10);
    public void Thema11() =&gt; ThemaButtonClicked(11);
    public void Thema12() =&gt; ThemaButtonClicked(12);
    public void Thema13() =&gt; ThemaButtonClicked(13);
    public void Thema14() =&gt; ThemaButtonClicked(14);
    public void Thema15() =&gt; ThemaButtonClicked(15);
    public void Thema16() =&gt; ThemaButtonClicked(16);
    public void Thema17() =&gt; ThemaButtonClicked(17);
    public void Thema18() =&gt; ThemaButtonClicked(18);
    public void Thema19() =&gt; ThemaButtonClicked(19);
    public void Press0() =&gt; Press(0);
    public void Press1() =&gt; Press(1);
    public void Press2() =&gt; Press(2);
    public void Press3() =&gt; Press(3);
    public void Press4() =&gt; Press(4);
    public void Press5() =&gt; Press(5);
    public void Press6() =&gt; Press(6);
    public void Press7() =&gt; Press(7);
    public void Press8() =&gt; Press(8);
    public void Press9() =&gt; Press(9);
    public void Press10() =&gt; Press(10);
    public void Press11() =&gt; Press(11);
    public void Press12() =&gt; Press(12);
    public void Press13() =&gt; Press(13);
    public void Press14() =&gt; Press(14);
    public void Press15() =&gt; Press(15);
    public void Press16() =&gt; Press(16);
    public void Press17() =&gt; Press(17);
    public void Press18() =&gt; Press(18);

    public void Press19()
    {
        Press(19);
    }
}</div>
</div>
</div>
</div>
</div>
<script class="__se_module_data" data-module='{"type":"v2_code", "id" : "SE-d353cfee-f9c7-416e-9cda-e1bf11561255"}' type="text/data"></script>
</div> <div class="se-component se-text se-l-default" id="SE-9ee0c67e-b9ad-44d2-abc1-1be0e39c2355">
<div class="se-component-content">
<div class="se-section se-section-text se-l-default">
<div class="se-module se-module-text">
<!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-dce1a2e9-1f51-4491-a602-20a811910671" style=""><span class="se-fs- se-ff-" id="SE-cd2c5624-727a-437b-b41b-40f5b4ee570f" style="">아래는 메인인 KoreaNews코드이다.</span></p><!-- } SE-TEXT --><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-6c55954e-f4a0-4254-80b2-b19666420c67" style=""><span class="se-fs- se-ff-" id="SE-e387e0a1-e32a-4e5e-8f3e-4702661ccfda" style="">​</span></p><!-- } SE-TEXT --><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-6eba206d-d9e7-431a-9825-f9cf945b769f" style=""><span class="se-fs- se-ff-" id="SE-21722616-5bc7-42d2-b51e-ea1c8e4c4adf" style="">우선 Start에서 언론사 이름의 숫자만큼 버튼을 켠다.</span></p><!-- } SE-TEXT --><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-1d40c287-ca1a-463c-9536-94be94e82e97" style=""><span class="se-fs- se-ff-" id="SE-6308bc66-91b8-4016-82ac-4b20c65ee690" style="">​</span></p><!-- } SE-TEXT --><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-9ade569f-22a1-4a2a-9721-84da600da727" style=""><span class="se-fs- se-ff-" id="SE-f703ba58-2bd7-47ef-8a02-af96ab43fddf" style="">언론사 버튼이 눌려지면 맨 아래 public void Press(int pressIndex)에서 언론사의 HTML을 가져온다.</span></p><!-- } SE-TEXT --><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-0f5b4110-9521-47ac-b4a3-7cc7234bcb84" style=""><span class="se-fs- se-ff-" id="SE-c2b9a829-ab19-4085-8b4a-cead5990aeec" style="">​</span></p><!-- } SE-TEXT --><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-a8c100f5-8a07-4073-bdfd-77a02a3aa5af" style=""><span class="se-fs- se-ff-" id="SE-eb5661d4-a0bf-4440-afa9-233306a7ab2b" style="">가져온 HTML은 OnStringLoadSuccess되어 Html태그를 제거하고 ^으로 테마를 구분해 테마 버튼의 이름을 바꾸고 켠다.</span></p><!-- } SE-TEXT --><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-a0060fbc-7a97-4dca-8a78-d5119dd93be8" style=""><span class="se-fs- se-ff-" id="SE-77e6c350-cfb7-457f-a683-008a0d982f80" style="">​</span></p><!-- } SE-TEXT --><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-913244d8-b661-486c-9773-3494a00d5669" style=""><span class="se-fs- se-ff-" id="SE-0f196e0b-fd33-4b79-a1c2-fbc413b841b8" style="">​</span></p><!-- } SE-TEXT --><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-5143ab14-03b2-4d10-8c6b-4a9c81fc8ef4" style=""><span class="se-fs- se-ff-" id="SE-f0735fcb-9c33-438e-9498-3a65ee57bf62" style="">테마 버튼을 선택하면 ThemaButtonClicked로 가서 SetPageIndexes를 돌리고 ShowPage한다.</span></p><!-- } SE-TEXT --><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-6821cd30-add8-4617-908e-8c61068edcc0" style=""><span class="se-fs- se-ff-" id="SE-982e6790-272b-4565-a125-c533c959d5db" style="">​</span></p><!-- } SE-TEXT --><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-eac4f89a-b495-412a-bd75-403a26f6ccc9" style=""><span class="se-fs- se-ff-" id="SE-cfaf97cf-d8cd-42b2-8781-25b2a4e6535d" style="">SetPageIndexes에서는 _(언더바)마다 나눠진 기사를 pagesize만큼 나눈 후, 각 페이지에서 어디까지 표시할지 인덱스를 저장한다.</span></p><!-- } SE-TEXT --><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-0d72aaec-d6b6-467a-9ab4-59dfe44a42fc" style=""><span class="se-fs- se-ff-" id="SE-438f8085-7d6e-4b8a-845d-7dc52914c9ad" style="">​</span></p><!-- } SE-TEXT --><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-81d73a35-c2f1-4558-b76b-38259a124981" style=""><span class="se-fs- se-ff-" id="SE-cb9c5534-e84e-4cb6-845d-420575057ef8" style="">사실 코드만 길 뿐이지 들어가는 로직은 없다.</span></p><!-- } SE-TEXT --><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-0ddb6bea-f93c-4618-a398-3352c8fcb5b1" style=""><span class="se-fs- se-ff-" id="SE-b0ae5cce-adce-446d-b735-6a6c407f391c" style="">​</span></p><!-- } SE-TEXT --><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-f7aeac6e-4832-4d6b-96e9-e31807dcd84f" style=""><span class="se-fs- se-ff-" id="SE-0a745113-5d35-4520-bd83-74c01f95416d" style="">생각치도 못한 숫자세기 문제와(마지막 인덱스가 넘치는 경우) 앞으로 멀티 플레이어를 위한 싱크를 제외하고는 </span></p><!-- } SE-TEXT --><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-ebef5509-b485-4bc2-9271-a2e28a6f21d8" style=""><span class="se-fs- se-ff-" id="SE-ae66db4e-dbaf-4c9a-8117-8478f90c3898" style="">​</span></p><!-- } SE-TEXT --><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-797683d9-f78a-4435-9a97-f59181b97612" style=""><span class="se-fs- se-ff-" id="SE-119120fa-3376-4c82-93be-e731b85f7eb9" style="">코드만 길 뿐이다.</span></p><!-- } SE-TEXT --><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-6773f4bb-f00c-400b-9e07-42e69259af7b" style=""><span class="se-fs- se-ff-" id="SE-8f2f0eea-e98e-49a7-8f8c-53cc10dad60e" style="">​</span></p><!-- } SE-TEXT --><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-9c74520a-7472-4cc1-924d-2cdb28d34ea2" style=""><span class="se-fs- se-ff-" id="SE-bcb40f9e-b01d-4365-a369-86e7218e260f" style="">막상 올리고 나니 주석하나 없는 코드가 사막마냥 황량해 보인다 ㅋㅋㅋ</span></p><!-- } SE-TEXT --><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-2521d416-38a8-4d59-a6d6-8941381fcac9" style=""><span class="se-fs- se-ff-" id="SE-4281d874-0845-40b8-bfc0-4097b252d47a" style="">​</span></p><!-- } SE-TEXT --><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-78309a5e-4f39-43a1-9033-7ec3abc4069f" style=""><span class="se-fs- se-ff-" id="SE-72a84fb4-b531-474a-bacb-e771090fb08b" style="">앞으로 시간이 난다면 해야 할 일은</span></p><!-- } SE-TEXT --><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-034a43a0-23d7-4d5d-a0da-184c3ff26b35" style=""><span class="se-fs- se-ff-" id="SE-95dea011-aa72-4d73-b396-234bf76a2fe5" style="">​</span></p><!-- } SE-TEXT --><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-38753eaa-b36f-4f95-9c4a-d7801107a975" style=""><span class="se-fs- se-ff-" id="SE-31f63fd6-9ce6-406e-91a8-15b4638952ed" style="">​</span></p><!-- } SE-TEXT --><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-1d22f51e-447a-4939-908d-1a3e84d901e5" style=""><span class="se-fs- se-ff-" id="SE-4ebf0b1a-5994-4437-a3ff-8096a14f07d7" style="">SubString(최적화): SubString은 가비지를 생성하므로 StringBuilder를 사용해야 한다. 그러나 VRChat에서는 StringBuilder가 사용불가능하다. 이를 해결하기 위해서는 Remove를 사용하거나 인덱스를 이용해 각 기사에 접근하는 방법을 이용해야 한다.</span></p><!-- } SE-TEXT --><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-0e717ca7-acc6-41f1-95ab-cc396c0d3eec" style=""><span class="se-fs- se-ff-" id="SE-6321fa5e-e337-4a01-9220-67ef5f5ae2d6" style="">​</span></p><!-- } SE-TEXT --><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-b234b766-bc9f-4dcb-9bc3-1e8ce31e77f9" style=""><span class="se-fs- se-ff-" id="SE-cf2ff05e-c438-45e9-bbeb-7ab6156b8bdb" style="">Sync: 다른 플레이어와의 Sync를 위해서는 현재 플레이어가 보고 있는 언론사,테마,페이지를 가져와야 한다.</span></p><!-- } SE-TEXT --><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-ca33ff9d-b6ea-4836-8422-a7f6bedc491a" style=""><span class="se-fs- se-ff-" id="SE-e1ad637e-e656-40a6-bdfd-3d9d81eeee9e" style="">HTML을 가져온 후 5초간 로드가 불가능하므로, 만약 다른 플레이어가 로드를 마친 후 페이지조작을 하면 String에서 오류가 날 수 있다.</span></p><!-- } SE-TEXT --><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-b3f2bc31-173a-4efb-ad76-d0a9f04cb4e0" style=""><span class="se-fs- se-ff-" id="SE-6c589bc6-aa8c-436d-8c52-502586caabc0" style="">이를 위한 예외처리를 해야 한다. VRChat에서 try catch가 불가능한것은 덤...</span></p><!-- } SE-TEXT --><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-79c00fa8-463e-4237-9387-8b4d8068ce8f" style=""><span class="se-fs- se-ff-" id="SE-a93399a3-bcd9-423b-a088-7d13bc192cf2" style="">​</span></p><!-- } SE-TEXT --><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-9c489900-b5b3-4b01-aac7-60dad2e4a26b" style=""><span class="se-fs- se-ff-" id="SE-ff3862f9-2ea7-4bd1-8749-3c94681f9908" style="">가볍게 시작한 일인데 하루가 후딱 지나가버렸다.</span></p><!-- } SE-TEXT --><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-f70d50cd-f915-468e-8ef2-5d11ff25c97e" style=""><span class="se-fs- se-ff-" id="SE-8d4c88e6-e4b6-4b87-a0f1-286155dc0032" style="">​</span></p><!-- } SE-TEXT --><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-ab594dda-9693-48f1-9c32-912a668146bc" style=""><span class="se-fs- se-ff-" id="SE-2b710d1f-928c-4561-8a72-03461d3680f2" style="">최근 졸업작품만 하다가 내가 하고싶은 것을 하니 조금 더 편안하긴 하다.</span></p><!-- } SE-TEXT --><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-943088f2-3171-44f4-9df6-cbee7d83a004" style=""><span class="se-fs- se-ff-" id="SE-93aa9e92-5c58-47bc-b9ee-1bc5594a979e" style="">​</span></p><!-- } SE-TEXT --><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-93ae0b81-58a8-4ea9-b449-a7c56358a429" style=""><span class="se-fs- se-ff-" id="SE-21f11e55-29f3-4b9c-8e6f-e98b9fd6aa4c" style="">​</span></p><!-- } SE-TEXT --><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-3294a6eb-5044-4794-af12-c8c2b42c81fc" style=""><span class="se-fs- se-ff-" id="SE-481bc2da-c469-459a-b7bd-b705e2682733" style="">react와 spring, node js도 공부해야 하는데 이건 언제쯤 손이 갈지...</span></p><!-- } SE-TEXT --><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-4ce52c4e-e070-4a48-acee-217f7e890014" style=""><span class="se-fs- se-ff-" id="SE-cc891d63-eab8-447e-b44a-bd4741fec253" style="">​</span></p><!-- } SE-TEXT --><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-a7886c8f-ff04-4fa3-9726-353e369ef844" style=""><span class="se-fs- se-ff-" id="SE-f74ac970-4759-4379-b5c2-2bf7db2eaf84" style="">​</span></p><!-- } SE-TEXT -->
</div>
</div>
</div>
</div> <div class="se-component se-image se-l-default" id="SE-1acbd0d1-51ec-4246-ad33-80a6a5c6ede5">
<div class="se-component-content se-component-content-fit">
<div class="se-section se-section-image se-l-default se-section-align-">
<div class="se-module se-module-image" style="">
<a class="se-module-image-link __se_image_link __se_link" data-linkdata='{"id" : "SE-1acbd0d1-51ec-4246-ad33-80a6a5c6ede5", "src" : "https://raw.githubusercontent.com/rage147-OwO/rage147-OwO.github.io/master/_images/images/2023-4-10-VRChatKoreaNews(Unity 파싱, 최적화)/0.png", "originalWidth" : "1918", "originalHeight" : "870", "linkUse" : "false", "link" : ""}' data-linktype="img" href="#" onclick="return false;" style="">
<img alt="" class="se-image-resource" src="https://raw.githubusercontent.com/rage147-OwO/rage147-OwO.github.io/master/_images/images/2023-4-10-VRChatKoreaNews(Unity 파싱, 최적화)/0.png">
</a>
</div>
</div>
</div>
</div>
<div class="se-component se-text se-l-default" id="SE-61ec6912-3701-4cb3-8b02-b1f998474518">
<div class="se-component-content">
<div class="se-section se-section-text se-l-default">
<div class="se-module se-module-text">
<!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-39501f0c-bbfa-42c7-a3df-25bf4595c383" style=""><span class="se-fs- se-ff-" id="SE-225e622f-1ffd-44a2-ae44-575f9e97521e" style="">​</span></p><!-- } SE-TEXT --><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-b392e1b7-5e60-4b77-a665-b5d55082db0d" style=""><span class="se-fs- se-ff-" id="SE-5ffc38ea-f8fe-4aa8-98aa-204dd627a447" style="">​</span></p><!-- } SE-TEXT -->
</div>
</div>
</div>
</div> </div>
</div>
</div>