---
title: "VRChat 에서 뉴스 보기 (RSS+github.io)"
categories:
 - personalproject
---
#VRChat 에서 뉴스 보기 (RSS+github.io) : 네이버 블로그
<div class="wrap_rabbit pcol2 _param(1) _postViewArea223070716515" id="post-view223070716515">
<!-- Rabbit HTML --><div class="se-viewer se-theme-default" lang="ko-KR">
<!-- SE_DOC_HEADER_END -->
<div class="se-main-container">
<div class="se-component se-quotation se-l-quotation_line" id="SE-b1db35be-bee0-43e1-bc0c-1b5de2a1af87">
<div class="se-component-content">
<div class="se-section se-section-quotation se-l-quotation_line">
<blockquote class="se-quotation-container">
<div class="se-module se-module-text se-quote"><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-423e1544-c851-4834-913a-eb0e4e2065eb" style=""><span class="se-fs- se-ff-" id="SE-0cbbc3ee-3049-4739-97fa-c0f6b22c2ed7" style="">들어가며</span></p><!-- } SE-TEXT --></div>
<div class="se-module se-module-text se-cite"><p class="se-text-paragraph se-text-paragraph-align-" id="SE-57c9687d-8568-4565-b819-f77f5080a8b2" style=""><span class="se-fs- se-ff-" id="SE-0258cd82-40f6-4736-a015-5100a18b4d7a" style="">VRChat 패치 소식: 웹에서 텍스트 가져오기 기능 추가됨!</span></p></div>
</blockquote>
</div>
</div>
</div>
<div class="se-component se-text se-l-default" id="SE-07d0c7da-28f4-4a2d-8a1c-b280b0bce3a9">
<div class="se-component-content">
<div class="se-section se-section-text se-l-default">
<div class="se-module se-module-text">
<!-- SE-TEXT { --><ul class="se-text-list se-text-list-type-bullet-disc"><li class="se-text-list-item"><p class="se-text-paragraph se-text-paragraph-align-" id="SE-d6630d63-b5d3-4eb3-97eb-1e67ad9842cf" style=""><span class="se-fs- se-ff-" id="SE-654204d5-6337-41f7-98a0-9afea9aebfa0" style=""><a class="se-link" href="https://docs.vrchat.com/docs/what-is-udon" target="_blank">VRChat에서는 Udon이라는 언어를 VM에서 실행할 수 있습니다.</a></span><span class="se-fs- se-ff-" id="SE-9b194747-a197-4589-b568-b681dd51bfb2" style=""> 이 Udon을 확장한 </span><span class="se-fs- se-ff-" id="SE-fe741e73-57ec-4723-9654-c22506bd0de1" style=""><a class="se-link" href="https://udonsharp.docs.vrchat.com/" target="_blank">UdonSharp</a></span><span class="se-fs- se-ff-" id="SE-c5c7d595-0ef8-4727-a7d5-a36c61e7d5a2" style="">는 C# 문법을 사용하여 VRChat 내부에서 게임이나 특정한 기능을 동작시킵니다. 다만, Udon에서 지원하지 않는 기능 중에는 대표적으로 웹과의 통신이 있습니다.</span></p></li></ul><p class="se-text-paragraph se-text-paragraph-align-" id="SE-e8f21a88-ce08-4080-b672-f94f9b144ed1" style=""><span class="se-fs- se-ff-" id="SE-7cb060fd-54b9-49ab-bec3-db0b0ceece2b" style="">​</span></p><ul class="se-text-list se-text-list-type-bullet-disc"><li class="se-text-list-item"><p class="se-text-paragraph se-text-paragraph-align-" id="SE-2babb179-cdb6-4c02-b258-820b5ff67ac1" style=""><span class="se-fs- se-ff-" id="SE-bbbfd940-c3f9-4bbb-9238-dc8c0b745c57" style="">따라서 유저들은 외부와 데이터 전송을 위해 디버그 로그를 통해 월드의 데이터를 외부로 빼거나, </span><span class="se-fs- se-ff-" id="SE-f4be61ee-1671-482e-9823-a13e9056211e" style=""><a class="se-link" href="https://feralresearch.org/lab/api-calls-from-inside-vrc/" target="_blank">웹 비디오 플레이어를 이용하여 데이터를 외부에서 받는 등</a></span><span class="se-fs- se-ff-" id="SE-69b7291d-d225-4369-8ba8-5350317f95b9" style=""> 다양한 꼼수를 개발해왔습니다.</span></p></li></ul><p class="se-text-paragraph se-text-paragraph-align-" id="SE-f7610e15-508a-4b99-98c1-cbbc7a735778" style=""><span class="se-fs- se-ff-" id="SE-7c56fd14-c253-440d-ae85-b73965001f0b" style="">​</span></p><ul class="se-text-list se-text-list-type-bullet-disc"><li class="se-text-list-item"><p class="se-text-paragraph se-text-paragraph-align-" id="SE-4c056238-c4aa-4fbb-914d-d755d244a257" style=""><span class="se-fs- se-ff-" id="SE-d167342e-2218-4890-87f1-5898d2383868" style="">약 반년 전, </span><span class="se-fs- se-ff-" id="SE-81879b50-f861-4c0e-a28f-8f14873e3280" style=""><a class="se-link" href="https://docs.vrchat.com/docs/osc-overview" target="_blank">아바타와 로컬 PC 간 통신이 가능한 OSC 프로토콜</a></span><span class="se-fs- se-ff-" id="SE-82859172-3216-49be-bd22-6ae0f9e6dcd0" style="">이 지원되면서 상황이 약간 개선되었습니다. 하지만 이는 월드용이 아닌 아바타용 프로토콜이기 때문에 월드 측면에서는 여전히 진전이 없었습니다.</span></p></li></ul><p class="se-text-paragraph se-text-paragraph-align-" id="SE-bfcbf418-fa9f-4086-8fb2-7f890a3e1850" style=""><span class="se-fs- se-ff-" id="SE-ec8d025e-9986-4fc2-8099-186256e9715e" style="">​</span></p><ul class="se-text-list se-text-list-type-bullet-disc"><li class="se-text-list-item"><p class="se-text-paragraph se-text-paragraph-align-" id="SE-d1be93b9-5ea6-45fe-86de-9d812500d068" style=""><span class="se-fs- se-ff-" id="SE-f404d09c-3901-4a70-b011-4df85d75a503" style="">그러던 중 2023년 3월 패치에서 </span><span class="se-fs- se-ff-" id="SE-05436c37-0203-40d2-a209-0292c4a9d067" style=""><a class="se-link" href="https://docs.vrchat.com/docs/string-loading" target="_blank">웹에서 텍스트를 가져오는</a></span><span class="se-fs- se-ff-" id="SE-718c2194-2077-4539-ab31-bf6decc14d98" style=""> 기능과 </span><span class="se-fs- se-ff-" id="SE-2c09809e-7802-4512-95c9-458e9d2fa918" style=""><a class="se-link" href="https://docs.vrchat.com/docs/image-loading" target="_blank">이미지를 가져오는</a></span><span class="se-fs- se-ff-" id="SE-fcd6d8d0-749f-4d5f-8438-20ce84a13724" style=""> 기능을 추가했습니다. </span></p></li></ul><p class="se-text-paragraph se-text-paragraph-align-" id="SE-c83cd199-acda-458f-97c6-230515d270bf" style=""><span class="se-fs- se-ff-" id="SE-cee8fc8e-5f6e-4268-85a2-779a2a8a776c" style="">​</span></p><p class="se-text-paragraph se-text-paragraph-align-" id="SE-d0fbade3-84c6-4337-9afc-005cf89fe001" style=""><span class="se-fs- se-ff-" id="SE-00880a25-abae-46c8-8d11-26e60dbbf375" style="">​</span></p><p class="se-text-paragraph se-text-paragraph-align-" id="SE-1c57e08a-3429-413c-a23c-c075b0e8abd1" style=""><span class="se-fs- se-ff-" id="SE-0fec7280-81e8-4780-93f9-edaacc16f630" style="">​</span></p><!-- } SE-TEXT -->
</div>
</div>
</div>
</div> <div class="se-component se-quotation se-l-quotation_line" id="SE-4eaf6559-f877-451b-8602-96533d8d84a8">
<div class="se-component-content">
<div class="se-section se-section-quotation se-l-quotation_line">
<blockquote class="se-quotation-container">
<div class="se-module se-module-text se-quote"><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-db8526bd-5169-4943-a4f5-d5c5998e458d" style=""><span class="se-fs- se-ff-" id="SE-9fe5bcec-4041-4db7-bb44-ab766ab26f34" style="">아이디어</span></p><!-- } SE-TEXT --></div>
<div class="se-module se-module-text se-cite"><p class="se-text-paragraph se-text-paragraph-align-" id="SE-5f0cdb57-7122-40f8-b265-05b5235e66d8" style=""><span class="se-fs- se-ff-" id="SE-728a7a79-d577-45c8-a9ad-325785085999" style="">무엇을 할까?</span></p></div>
</blockquote>
</div>
</div>
</div>
<div class="se-component se-text se-l-default" id="SE-4557cfc2-e54e-4748-8acc-887976cdb4bf">
<div class="se-component-content">
<div class="se-section se-section-text se-l-default">
<div class="se-module se-module-text">
<!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-990592dd-1739-406e-afe8-c0e27b606edb" style=""><span class="se-fs- se-ff-" id="SE-1efb6907-55c3-4dc7-ad71-8bdbe4f6bc84" style="">VRChat에서 웹과 통신이 가능해지면서 많은 가능성이 열렸습니다. 예를 들어, 새로운 RPG 월드에서 SQL 데이터 테이블과 연동하여 플레이어 정보를 저장할 수 있고, 카지노 월드에서는 자신의 소지금 외부에 저장할 수 있습니다. 또한 실시간으로 주식 정보도 가져올 수 있겠네요.</span></p><p class="se-text-paragraph se-text-paragraph-align-" id="SE-cec05036-b1aa-48d7-ae02-c22b9a86dfd4" style=""><span class="se-fs- se-ff-" id="SE-ff0be54c-e114-44a1-adba-c6bdc5d81902" style="">​</span></p><p class="se-text-paragraph se-text-paragraph-align-" id="SE-49b2bf46-d477-45e1-8914-80c66052485b" style=""><span class="se-fs- se-ff-" id="SE-d2da4060-69d1-455a-8476-f0842cb5edf8" style="">필자는 VRChat에서 무엇을 가져올까? 고민고민하다 뉴스를 가져오는 기능을 추가하기로 결정했습니다. 이를 위해 해야 할 과정을 생각해보자면 다음과 같습니다:</span></p><p class="se-text-paragraph se-text-paragraph-align-" id="SE-f258b35c-4794-478c-8480-ac8be2b9a459" style=""><span class="se-fs- se-ff-" id="SE-c851a969-d188-42c8-a23b-d8d57607fc6d" style="">​</span></p><ol class="se-text-list se-text-list-type-decimal"><li class="se-text-list-item"><p class="se-text-paragraph se-text-paragraph-align-" id="SE-4325d568-5a1f-4e00-b8ce-cf95545e11e9" style=""><span class="se-fs- se-ff-" id="SE-e603bd06-ebc1-4245-a4fa-f8f7d19b8ebe" style="">다양한 언론사의 뉴스를 가공해서 웹에 올리기</span></p></li><li class="se-text-list-item"><p class="se-text-paragraph se-text-paragraph-align-" id="SE-dafb7fe0-2eb0-44dd-aa3c-97dbfbeb631e" style=""><span class="se-fs- se-ff-" id="SE-b7bbd79a-9009-44fb-b466-0d60dc48f2fe" style="">웹에서 텍스트를 받아 구문분석(parsing)하기</span></p></li></ol><p class="se-text-paragraph se-text-paragraph-align-" id="SE-7281e02b-1ab6-475c-bd5a-95973308ad23" style=""><span class="se-fs- se-ff-" id="SE-97b6021f-ccbc-423e-9c40-3dba62dda5e9" style="">​</span></p><p class="se-text-paragraph se-text-paragraph-align-" id="SE-d8248208-5f52-49c0-8d18-a10ceae2eedc" style=""><span class="se-fs- se-ff-" id="SE-eec6cf7f-ae48-4c63-99ef-0b24bf04ed12" style="">​</span></p><p class="se-text-paragraph se-text-paragraph-align-" id="SE-19702828-5c6b-4daf-8716-f32b60e23613" style=""><span class="se-fs- se-ff-" id="SE-74760ff9-9d13-455c-9555-5b7e2022f6ec" style="">​</span></p><!-- } SE-TEXT -->
</div>
</div>
</div>
</div> <div class="se-component se-quotation se-l-quotation_line" id="SE-839035f0-3044-4fc8-b550-96bad131c93c">
<div class="se-component-content">
<div class="se-section se-section-quotation se-l-quotation_line">
<blockquote class="se-quotation-container">
<div class="se-module se-module-text se-quote"><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-27c3c9b4-d49e-488a-8cd7-3a3e8f06a5bf" style=""><span class="se-fs- se-ff-" id="SE-0df5fed0-08cf-4533-8212-625fd118106a" style="">StringLoading 맛보기</span></p><!-- } SE-TEXT --></div>
<div class="se-module se-module-text se-cite"><p class="se-text-paragraph se-text-paragraph-align-" id="SE-681423d3-34fd-4db2-83fc-27559b6be69c" style=""><span class="se-fs- se-ff-" id="SE-2f6c8e27-be38-4007-b438-91564f94dbbd" style="">이젠 이미지도 불러올수 있다구</span></p></div>
</blockquote>
</div>
</div>
</div>
<div class="se-component se-text se-l-default" id="SE-d069607c-8d92-4640-8df4-bfc9382d6be7">
<div class="se-component-content">
<div class="se-section se-section-text se-l-default">
<div class="se-module se-module-text">
<!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-3ee8426d-0db3-4e6c-a813-62b7c2ad12e7" style=""><span class="se-fs- se-ff-" id="SE-c8d63f78-405a-484d-ba99-ddb416770996" style="">이번에 추가된 </span><span class="se-fs- se-ff-" id="SE-0a1d92e6-d2d1-4f6c-9777-2285efb69021" style=""><a class="se-link" href="https://docs.vrchat.com/docs/string-loading" target="_blank">StringLoading 문서</a></span><span class="se-fs- se-ff-" id="SE-f032ff51-f316-4b2f-8fbd-7b292d1e1698" style="">를 보면, </span></p><ul class="se-text-list se-text-list-type-bullet-disc"><li class="se-text-list-item"><p class="se-text-paragraph se-text-paragraph-align-" id="SE-bce4872d-f12f-4064-a8d9-604f7461c0f2" style=""><span class="se-fs- se-ff-" id="SE-e7b70dfa-7045-48ed-b5f7-3c1d7ab9b50c" style="">5초에 하나의 문자열(링크)만 다운로드 가능</span></p></li><li class="se-text-list-item"><p class="se-text-paragraph se-text-paragraph-align-" id="SE-1fadead1-0507-4a31-be92-753b4ac7b144" style=""><span class="se-fs- se-ff-" id="SE-5a480d54-f12e-4fd5-ac26-9180364fcb29" style="">한 문자열은 최대 100MB</span></p></li><li class="se-text-list-item"><p class="se-text-paragraph se-text-paragraph-align-" id="SE-cd6d7dd6-22e3-43f3-9c24-345cdafdbf8d" style=""><span class="se-fs- se-ff-" id="SE-ac166bd4-554d-4b12-ad17-d870389724fd" style="">대기열은 최대 1000개</span></p></li><li class="se-text-list-item"><p class="se-text-paragraph se-text-paragraph-align-" id="SE-442e9dd3-219f-4767-9ed3-2411b4562114" style=""><span class="se-fs- se-ff-" id="SE-517ab241-0c8d-4c05-837c-7e84105e3b66" style="">신뢰하는 URL은 (*.github.io, pastebin.com,gist.githubusercontent.com)이다. 꼭 이 도메인이 아니더라도 유저가 '</span><span class="se-fs-fs15 se-ff-system se-style-unset" id="SE-19642635-738b-4b32-aef5-08652812743b" style="color:#384248;background-color:#ffffff;">Allow Untrusted URLs’옵션을 키면, 다른 도메인도 가능하다.</span></p></li></ul><p class="se-text-paragraph se-text-paragraph-align-" id="SE-d1aea482-ddc9-4ee3-9af8-ff1784dbbeb6" style=""><span class="se-fs-fs15 se-ff-system se-style-unset" id="SE-ba96eefa-2f7c-41ae-9344-3f097d0e7f4e" style="color:#384248;">​</span></p><p class="se-text-paragraph se-text-paragraph-align-" id="SE-7df9cb7b-af43-4c24-af5a-b16ec45e5155" style=""><span class="se-fs-fs15 se-ff-system se-style-unset" id="SE-4b82edbe-5cca-46e4-a8dc-7311173bf6a4" style="color:#384248;background-color:#ffffff;">추가된 노드로는 </span></p><p class="se-text-paragraph se-text-paragraph-align-" id="SE-2e3a7a1c-36c9-4440-8b54-b4586eb50f88" style=""><span class="se-fs-fs15 se-ff-system se-style-unset" id="SE-a0f1c139-cb55-418b-bff8-537659fc2cfb" style="color:#384248;">​</span></p><ul class="se-text-list se-text-list-type-bullet-disc"><li class="se-text-list-item"><p class="se-text-paragraph se-text-paragraph-align-" id="SE-c0238379-f3a3-4f4c-b563-ec8d9b401420" style=""><span class="se-fs-fs15 se-ff-system se-style-unset" id="SE-66c05d82-1413-44d0-9f97-6b77a4630e5d" style="color:#384248;background-color:#ffffff;">이벤트</span></p><ul class="se-text-list se-text-list-type-bullet-circle"><li class="se-text-list-item"><p class="se-text-paragraph se-text-paragraph-align-" id="SE-122c3e79-7df3-4f56-a672-1f276b298c91" style=""><span class="se-fs-fs15 se-ff-system se-style-unset" id="SE-530ccf36-e663-462f-9cb4-14c9bc65f6e0" style="color:#384248;background-color:#ffffff;">OnStringLoadSuccess</span></p></li><li class="se-text-list-item"><p class="se-text-paragraph se-text-paragraph-align-" id="SE-9cd391df-6426-4965-a406-4ad637fbb856" style=""><span class="se-fs-fs15 se-ff-system se-style-unset" id="SE-5c57b046-0c8e-4989-b67f-2a31adde70bc" style="color:#384248;background-color:#ffffff;">OnStringLoadError</span></p></li></ul></li><li class="se-text-list-item"><p class="se-text-paragraph se-text-paragraph-align-" id="SE-8d2d4102-3844-4eb7-80bd-64c31368f862" style=""><span class="se-fs-fs15 se-ff-system se-style-unset" id="SE-25db3e91-aa4d-4793-a2f2-28f0d79ed308" style="color:#384248;background-color:#ffffff;">VRCStringDownloader.LoadUrl(Url , UdonBehaviour)</span></p><ul class="se-text-list se-text-list-type-bullet-circle"><li class="se-text-list-item"><p class="se-text-paragraph se-text-paragraph-align-" id="SE-0ae52cea-b6ee-4c17-abf2-9c686293e62f" style=""><span class="se-fs-fs15 se-ff-system se-style-unset" id="SE-fc098374-45b9-4f11-a0e0-4b40358093c0" style="color:#384248;background-color:#ffffff;">String을 가져오는 노드이다</span></p></li><li class="se-text-list-item"><p class="se-text-paragraph se-text-paragraph-align-" id="SE-7123d388-b7f1-4ede-b7e4-2ddf5f26de18" style=""><span class="se-fs-fs15 se-ff-system se-style-unset" id="SE-1735beb6-3309-4f2d-b621-3b1c13f82f49" style="color:#384248;background-color:#ffffff;">Url은 String을 가져올 링크, UdonBehaviour는 링크를 가져왔을 때 이벤트(OnStringLoad)가 실행될 대상이다</span></p></li></ul></li><li class="se-text-list-item"><p class="se-text-paragraph se-text-paragraph-align-" id="SE-c321b207-5112-4f45-8bfe-87fb37a61658" style=""><span class="se-fs-fs15 se-ff-system se-style-unset" id="SE-66442a3a-cf93-4bc2-a4e8-e9a2c7fafb92" style="color:#384248;background-color:#ffffff;">IVRCStringDownload  : String을 가져온 Result입니다</span></p><ul class="se-text-list se-text-list-type-bullet-circle"><li class="se-text-list-item"><p class="se-text-paragraph se-text-paragraph-align-" id="SE-36934d51-2662-420b-aaa6-e5974e872cdf" style=""><span class="se-fs-fs15 se-ff-system se-style-unset" id="SE-b97f4270-bd45-40bf-8fcc-3b94c3467aed" style="color:#384248;background-color:#ffffff;">Error : Load에 대한 오륲 메시지를 가져옵니다</span></p></li><li class="se-text-list-item"><p class="se-text-paragraph se-text-paragraph-align-" id="SE-d0d73671-abe9-4008-92a5-a109918c6e05" style=""><span class="se-fs-fs15 se-ff-system se-style-unset" id="SE-40a22c57-ac56-431c-a51d-881a40b194d3" style="color:#384248;background-color:#ffffff;">ErrorCode : Load에 대한 HTTP오류 코드를 가져옵니다</span></p></li><li class="se-text-list-item"><p class="se-text-paragraph se-text-paragraph-align-" id="SE-a9115799-70e2-4687-bf28-f9c70f51fd5a" style=""><span class="se-fs-fs15 se-ff-system se-style-unset" id="SE-2ead289a-99f4-4500-9a03-a9239021ac2e" style="color:#384248;background-color:#ffffff;">Response : 다운로드된 문자열</span></p></li><li class="se-text-list-item"><p class="se-text-paragraph se-text-paragraph-align-" id="SE-ee03363f-4b4f-48d4-8380-012ec60e3f02" style=""><span class="se-fs-fs15 se-ff-system se-style-unset" id="SE-f2f46cab-2666-4f61-8d81-5b88c384e263" style="color:#384248;background-color:#ffffff;">UdonBehaviour : Load이벤트를 전송할 UdonBehaviour</span></p></li></ul></li></ul><p class="se-text-paragraph se-text-paragraph-align-" id="SE-2e5933ee-384a-41ce-ab8e-cf1ae830286b" style=""><span class="se-fs-fs15 se-ff-system se-style-unset" id="SE-df780f62-7366-43db-85aa-dca5a844e987" style="color:#384248;">​</span></p><p class="se-text-paragraph se-text-paragraph-align-" id="SE-f73250f7-a1bc-4424-8740-1833105dc821" style=""><span class="se-fs-fs15 se-ff-system se-style-unset" id="SE-a7f53361-2407-49bb-88a0-8308cd9349c4" style="color:#384248;background-color:#ffffff;">주의할 점은</span><span class="se-fs-fs15 se-ff-system se-style-unset" id="SE-6fac46a7-78b8-44bb-8b37-e307eee747f4" style="color:#384248;background-color:#ffffff;"><b> UdonSharp</b></span><span class="se-fs-fs15 se-ff-system se-style-unset" id="SE-6ea634d3-c6f1-42b9-8c2e-1774c125f26c" style="color:#384248;background-color:#ffffff;">를 사용해서 코드를 작성할 때 </span></p><p class="se-text-paragraph se-text-paragraph-align-" id="SE-d381f3cd-9c6c-4546-bb89-b38d613b6c9c" style=""><span class="se-fs- se-ff-system se-style-unset" id="SE-55750c0d-f298-494b-8bfd-0011633b5ba8" style="color:#384248;background-color:#ffffff;">VRC.SDK3.StringLoading.VRCStringDownloader.LoadUrl(Url)을 해도 컴파일 오류가 나지는 않지만, 실행 중 이벤트를 보낼 타겟이 null로 되어 있어 오류가 납니다.</span></p><p class="se-text-paragraph se-text-paragraph-align-" id="SE-75e9ebe4-1038-4b8f-8b9e-d29f2411cc8c" style=""><span class="se-fs- se-ff-system se-style-unset" id="SE-4a6d48e3-f635-4dc7-b53b-d03f72bb84e5" style="color:#384248;">​</span></p><p class="se-text-paragraph se-text-paragraph-align-" id="SE-375f4224-c8ee-42b4-ba80-1bc4b9193020" style=""><span class="se-fs- se-ff-system se-style-unset" id="SE-9efa0c2a-2f38-4c0d-8b6e-d305873780eb" style="color:#384248;background-color:#ffffff;">그렇기에 VRC.SDK3.StringLoading.VRCStringDownloader.LoadUrl(Url,</span><span class="se-fs- se-ff-system se-style-unset" id="SE-0ec2f2c1-fdf6-4bde-a811-91ef35547e9a" style="color:#384248;background-color:#ffffff;"><b>GetComponent&lt;UdonBehaviour&gt;()</b></span><span class="se-fs- se-ff-system se-style-unset" id="SE-487b7ded-e293-4225-b553-cbc0fe26d404" style="color:#384248;background-color:#ffffff;">)로 이벤트를 받을 대상을 지정해줘야 합니다.</span></p><p class="se-text-paragraph se-text-paragraph-align-" id="SE-e87740d0-d53e-44a9-8ec9-414e81adcdd0" style=""><span class="se-fs- se-ff-system se-style-unset" id="SE-f0a38bb4-e0ad-4d35-a3d1-415ca2d17fd1" style="color:#384248;">​</span></p><p class="se-text-paragraph se-text-paragraph-align-" id="SE-34dbd6c3-3174-4f73-a67e-4f58ed7e6242" style=""><span class="se-fs- se-ff-system se-style-unset" id="SE-da0198f0-e694-4e9a-bc14-4a982d891096" style="color:#384248;">​</span></p><p class="se-text-paragraph se-text-paragraph-align-" id="SE-cb5c8d80-c466-4fcc-aed6-27c9b5f89bd9" style=""><span class="se-fs-fs15 se-ff-system se-style-unset" id="SE-77517a7b-fda1-4828-907d-544b4e973e70" style="color:#384248;">​</span></p><p class="se-text-paragraph se-text-paragraph-align-" id="SE-c62d782a-0c71-454e-b43c-e2b303482669" style=""><span class="se-fs-fs15 se-ff-system se-style-unset" id="SE-2f8b2160-8293-466f-adad-152ee6168cf4" style="color:#384248;background-color:#ffffff;">아래는 링크를 로드해 디버그 로그로 띄우는 코드입니다</span></p><p class="se-text-paragraph se-text-paragraph-align-" id="SE-0e38b577-86c7-44b8-b479-45829eb9c35b" style=""><span class="se-fs-fs15 se-ff-system se-style-unset" id="SE-35fabaf8-83cd-4085-a08f-fad8cd580f13" style="color:#384248;background-color:#ffffff;">UdonGraph</span></p><!-- } SE-TEXT -->
</div>
</div>
</div>
</div> <div class="se-component se-image se-l-default" id="SE-3a8db959-ea19-4aba-9d54-b18a34882335">
<div class="se-component-content se-component-content-fit">
<div class="se-section se-section-image se-l-default se-section-align-">
<div class="se-module se-module-image" style="">
<a class="se-module-image-link __se_image_link __se_link" data-linkdata='{"id" : "SE-3a8db959-ea19-4aba-9d54-b18a34882335", "src" : "https://postfiles.pstatic.net/MjAyMzA0MTNfMTc3/MDAxNjgxMzc1MTcxNzgw.howOZk0s8geGgxXcIDofovSeZ8-3MpvtSOE304R9BEIg.tzjOL5QFMPUaWoeO5ZE8sFrpYRGrBbd5SpYwiyvOjBUg.PNG.dls32208/image.png", "originalWidth" : "1448", "originalHeight" : "751", "linkUse" : "false", "link" : ""}' data-linktype="img" href="#" onclick="return false;" style="">
<img alt="" class="se-image-resource" data-height="359" data-lazy-src="https://postfiles.pstatic.net/MjAyMzA0MTNfMTc3/MDAxNjgxMzc1MTcxNzgw.howOZk0s8geGgxXcIDofovSeZ8-3MpvtSOE304R9BEIg.tzjOL5QFMPUaWoeO5ZE8sFrpYRGrBbd5SpYwiyvOjBUg.PNG.dls32208/image.png?type=w773" data-width="693" src="https://raw.githubusercontent.com/rage147-OwO/rage147-OwO.github.io/master/_images/images/2023-4-10-VRChat 에서 뉴스 보기 (RSS+github.io)/0.png">
</a>
</div>
</div>
</div>
</div>
<div class="se-component se-code se-l-code_black" id="SE-5ffb98cf-951a-4606-b55d-c7bdc4b40fce">
<div class="se-component-content">
<div class="se-section se-section-code se-l-code_black">
<div class="se-module se-module-code se-fs-fs13">
<div class="se-code-source">
<div class="__se_code_view language-javascript">application/vnd.unity.graphview.elements AM2W227bRhCGX8XYay2x54MB38RKCyFBU9ixchEYwp4osKGWBQ9ODSdP1os+Ul+hI1FyGkkohMQuAupCXO4uZ/6Z/+P+/edfD+jO1UNC5+8fUDnU9S9uBTdo7trK+Tot5leX19NXL1yX4N9NW6MJGqoIMwQP0QhDcEkFwSJ4ji2hFCvDeLJMCmsJTP696aq+ajI6f0B/oHPMrSiU5pZapbXmQkzQPQxTTQpBORGEKko5M58nKDcx3cymHcSGYKcvv9sJKuvm4/bZ7Thzvk6j2+Qx5Kq/f+N/S6Gfj8k9oCp3vcshzabonMDmXd9Webl9jNDnybcsu77v+rQqrjeDk7NVF5q2rvzkbJ7aDpK+EAVZX5Ozy6HuhzZd5DT0rasnZ78Ovq7Cq3T/tvmQ8oXX2skgFbVcJGLsp3fJv67yh+8L7EXT1Mnlp43sbQuv+PHC+snV3XfG9Rx1zE2GqG7Xcf3LXi/vUu4Xs9yn1oX+0VOJyFIkobE3kmPBBMWeOI2jjYwTuDzhRzzFwDzUSqWNpsRyLbeeUrSQX/voa+egQGFDmkosnEtYyKSxcyri4KIJxjtuVIn2/bWfy0gIPor3unFxLSyMbe6nzcdcw1hqi8Vi/RAQsjiAynrgJjb5slmtmryRpXQhdbP14EarqxRSdZfaxWKs1bwBwXaynZTGgWzMFpQYYBGxUsN6pnYo0oWxlFkF6zQ1Wu2xyBvQOZYl1oxHIB/gz8cUcDQslJEkxoj5RA5BhQ6k/B9RddiDP6d+scP8o5Sn5HasAxkrtIJ+F1pLbonio5ZKFwxYz6UWDJSU+1R/epI/o5VP+uI9VXVu1nu8zMsqp2nyw3Jjn+Wu/cfNj5rBKKp4qQN2sdyYwWBDpcXwYYUu91LGkh0xwxYhwkC6XNrtZ9luqqoEk9pQtl8+ZWhMSXgQJEKzeOaxKwnFwYeSMCoNUe6YEX4oG4wofpO/8Ot6CMCe7lFRqmRMKkpcptJgoRIFvNgSc+2dVtKlYOMxT3BTKDjRCM2BIVaOluB2c/zhwnIlGZx//hPQJxXzWwA9OyA0NNgSiHCVOvDFrrPGKY9KnFLwQyWMKgjkShVRQkhORyG2mOWUKiEl0fsnvlNUh+Z6js66hesf</div>
</div>
</div>
</div>
</div>
<script class="__se_module_data" data-module='{"type":"v2_code", "id" : "SE-5ffb98cf-951a-4606-b55d-c7bdc4b40fce"}' type="text/data"></script>
</div> <div class="se-component se-text se-l-default" id="SE-524b3a3b-12ba-40e0-9207-25434870438c">
<div class="se-component-content">
<div class="se-section se-section-text se-l-default">
<div class="se-module se-module-text">
<!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-9f1d60f9-215b-4aa5-bb18-f25f520aa6fe" style=""><span class="se-fs- se-ff-" id="SE-a91c04a9-cd0d-4de3-8a0f-0c7daeb623e7" style="">​</span></p><!-- } SE-TEXT --><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-967dc884-e68b-442a-9de2-74e53103ac23" style=""><span class="se-fs- se-ff-" id="SE-9db47cfe-92b0-46ae-8433-6dae4923a08a" style="">​</span></p><!-- } SE-TEXT --><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-65eb8b41-9e23-4682-a40a-45666982af67" style=""><span class="se-fs- se-ff-" id="SE-8b379115-962f-4347-9ee2-e9ef6065c88c" style="">​</span></p><!-- } SE-TEXT --><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-26ccf5e1-dbd7-4a28-9dd1-1c6f6088c075" style=""><span class="se-fs- se-ff-" id="SE-90931305-3dc7-4933-a749-84bf2aa95c7a" style="">​</span></p><!-- } SE-TEXT --><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-a735ed48-692e-4b2c-a89a-c759146f74d8" style=""><span class="se-fs- se-ff-" id="SE-fce00ffd-d12b-4e32-934f-b59c5c4c44cc" style="">​</span></p><!-- } SE-TEXT --><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-755ca16a-8fd1-49a3-9798-ae2e5f026ffc" style=""><span class="se-fs- se-ff-" id="SE-f011f4b7-9145-474c-be8a-be29d4fed056" style="">UdonSharp</span></p><!-- } SE-TEXT -->
</div>
</div>
</div>
</div> <div class="se-component se-image se-l-default" id="SE-3b36523e-98e8-4fe8-8e04-86b932e373e1">
<div class="se-component-content se-component-content-fit">
<div class="se-section se-section-image se-l-default se-section-align-">
<div class="se-module se-module-image" style="">
<a class="se-module-image-link __se_image_link __se_link" data-linkdata='{"id" : "SE-3b36523e-98e8-4fe8-8e04-86b932e373e1", "src" : "https://postfiles.pstatic.net/MjAyMzA0MTNfMjQ5/MDAxNjgxMzc2MDI4NDk3.L9r85zVrVycwM5Sg9Dg9aUzW1_WtiO6LFzwblMvsksMg.rwxBHrwinYGVm_ZxzqKShBNsMLu4zhAcGtcJLcdiLvYg.PNG.dls32208/image.png", "originalWidth" : "931", "originalHeight" : "681", "linkUse" : "false", "link" : ""}' data-linktype="img" href="#" onclick="return false;" style="">
<img alt="" class="se-image-resource" data-height="506" data-lazy-src="https://postfiles.pstatic.net/MjAyMzA0MTNfMjQ5/MDAxNjgxMzc2MDI4NDk3.L9r85zVrVycwM5Sg9Dg9aUzW1_WtiO6LFzwblMvsksMg.rwxBHrwinYGVm_ZxzqKShBNsMLu4zhAcGtcJLcdiLvYg.PNG.dls32208/image.png?type=w773" data-width="693" src="https://raw.githubusercontent.com/rage147-OwO/rage147-OwO.github.io/master/_images/images/2023-4-10-VRChat 에서 뉴스 보기 (RSS+github.io)/1.png">
</a>
</div>
</div>
</div>
</div>
<div class="se-component se-code se-l-code_black" id="SE-fb7fdb7d-c3ab-4037-a5a9-423e60d6dbbe">
<div class="se-component-content">
<div class="se-section se-section-code se-l-code_black">
<div class="se-module se-module-code se-fs-fs13">
<div class="se-code-source">
<div class="__se_code_view language-javascript">using System;
using UdonSharp;
using UnityEngine;
using VRC.SDK3.StringLoading;
using VRC.SDKBase;
using VRC.Udon;

public class Test : UdonSharpBehaviour
{

    VRCUrl adf= new VRCUrl("https://feralresearch.org/lab/api-calls-from-inside-vrc/");
    public override void Interact()
    {
        VRC.SDK3.StringLoading.VRCStringDownloader.LoadUrl(adf,gameObject.GetComponent&lt;UdonBehaviour&gt;());
    }

    public override void OnStringLoadSuccess(IVRCStringDownload result)
    {
        Debug.Log(result.Result);
    }

    
}
</div>
</div>
</div>
</div>
</div>
<script class="__se_module_data" data-module='{"type":"v2_code", "id" : "SE-fb7fdb7d-c3ab-4037-a5a9-423e60d6dbbe"}' type="text/data"></script>
</div> <div class="se-component se-text se-l-default" id="SE-cd8a7ea6-766f-4027-ada8-7d3ed021f0ea">
<div class="se-component-content">
<div class="se-section se-section-text se-l-default">
<div class="se-module se-module-text">
<!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-93c0d80a-97ca-47e8-9501-163cac65dc59" style=""><span class="se-fs-fs15 se-ff-system se-style-unset" id="SE-0b65f575-1892-4882-864f-98ad4f288958" style="color:#384248;">​</span></p><!-- } SE-TEXT --><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-5db9d013-d424-4fc2-b7d8-9f04dd68939f" style=""><span class="se-fs-fs15 se-ff-system se-style-unset" id="SE-bf4f7985-7816-4640-b403-649e53865e66" style="color:#384248;">​</span></p><!-- } SE-TEXT --><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-ab057394-8d77-49cd-a749-4f2dbcd5b314" style=""><span class="se-fs-fs15 se-ff-system se-style-unset" id="SE-114e377a-6de2-41c3-8554-c53712d73534" style="color:#384248;">​</span></p><!-- } SE-TEXT --><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-77a0cf6f-dfb3-4f41-967b-67e02123407a" style=""><span class="se-fs-fs15 se-ff-system se-style-unset" id="SE-d77ea957-05a2-43fc-ad7e-53da13b22861" style="color:#384248;">​</span></p><!-- } SE-TEXT --><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-f6e990a3-3bd2-4499-9b93-333d91175d5b" style=""><span class="se-fs-fs15 se-ff-system se-style-unset" id="SE-ea365ba6-4204-448f-bdaa-f8b6a5ee4eb6" style="color:#384248;">​</span></p><!-- } SE-TEXT -->
</div>
</div>
</div>
</div> <div class="se-component se-quotation se-l-quotation_line" id="SE-9363e828-21cf-4ee0-9d18-7536548fabe4">
<div class="se-component-content">
<div class="se-section se-section-quotation se-l-quotation_line">
<blockquote class="se-quotation-container">
<div class="se-module se-module-text se-quote"><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-fa6c9135-44d3-4398-a8bd-9eb3c7537c0b" style=""><span class="se-fs- se-ff-" id="SE-cb69d5d3-115a-4228-8b69-6c8f0412bf18" style="">자바스크립트로 RSS불러오기</span></p><!-- } SE-TEXT --></div>
<div class="se-module se-module-text se-cite"><p class="se-text-paragraph se-text-paragraph-align-" id="SE-f0276166-701f-4662-802f-144c18706fb8" style=""><span class="se-fs- se-ff-" id="SE-0002760c-d866-4eef-9c58-c697bb8bd5ef" style="">바보같은 결과가 나왔다!</span></p></div>
</blockquote>
</div>
</div>
</div>
<div class="se-component se-text se-l-default" id="SE-2a9bcd68-2382-49f3-a840-d9bd0e672b57">
<div class="se-component-content">
<div class="se-section se-section-text se-l-default">
<div class="se-module se-module-text">
<!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-1eaf86da-58f6-4c17-af30-9a9757460fb8" style=""><span class="se-fs- se-ff-system se-style-unset" id="SE-b1fa0260-ecdc-4703-8582-42952b0c14fe" style="color:#384248;background-color:#ffffff;">우선 깃허브 리포지토리를 하나 만들고, Github Pages를 설정합니다</span></p><!-- } SE-TEXT -->
</div>
</div>
</div>
</div> <div class="se-component se-image se-l-default" id="SE-89436ec3-6b2f-45c3-8bdc-f9e5e88374b1">
<div class="se-component-content se-component-content-fit">
<div class="se-section se-section-image se-l-default se-section-align-">
<div class="se-module se-module-image" style="">
<a class="se-module-image-link __se_image_link __se_link" data-linkdata='{"id" : "SE-89436ec3-6b2f-45c3-8bdc-f9e5e88374b1", "src" : "https://postfiles.pstatic.net/MjAyMzA0MTNfNzgg/MDAxNjgxMzc3MTc4MTY3.QpgjYAwYWlLnI95ozeoOZ3pFC8BdS-5Q64T6Io_XDsgg.xIBW-dhEB1Xw0vKwwDRAbiGB41yCzVGtzFLngQGxEjMg.PNG.dls32208/image.png", "originalWidth" : "1435", "originalHeight" : "753", "linkUse" : "false", "link" : ""}' data-linktype="img" href="#" onclick="return false;" style="">
<img alt="" class="se-image-resource" data-height="363" data-lazy-src="https://postfiles.pstatic.net/MjAyMzA0MTNfNzgg/MDAxNjgxMzc3MTc4MTY3.QpgjYAwYWlLnI95ozeoOZ3pFC8BdS-5Q64T6Io_XDsgg.xIBW-dhEB1Xw0vKwwDRAbiGB41yCzVGtzFLngQGxEjMg.PNG.dls32208/image.png?type=w773" data-width="693" src="https://raw.githubusercontent.com/rage147-OwO/rage147-OwO.github.io/master/_images/images/2023-4-10-VRChat 에서 뉴스 보기 (RSS+github.io)/2.png">
</a>
</div>
</div>
</div>
</div>
<div class="se-component se-text se-l-default" id="SE-bff7364d-7406-4a3e-af66-32c7ddcc37d1">
<div class="se-component-content">
<div class="se-section se-section-text se-l-default">
<div class="se-module se-module-text">
<!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-58f1c479-aa4d-425a-8bdd-11517bd264fa" style=""><span class="se-fs- se-ff-system se-style-unset" id="SE-7190bbed-4cfc-4bf6-ba35-9a9d249c063a" style="color:#384248;">​</span></p><!-- } SE-TEXT --><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-c5ea8518-244a-4423-9585-ec64d81ca358" style=""><span class="se-fs- se-ff-system se-style-unset" id="SE-5e904ffe-49e4-4738-983e-c1b0c85931d3" style="color:#384248;background-color:#ffffff;">그리고서 rss를 가져오는 자바스크립트를 html로 커밋합니다</span></p><!-- } SE-TEXT -->
</div>
</div>
</div>
</div> <div class="se-component se-code se-l-code_black" id="SE-2267a7b3-27c8-445c-81b2-34299352792e">
<div class="se-component-content">
<div class="se-section se-section-code se-l-code_black">
<div class="se-module se-module-code se-fs-fs13">
<div class="se-code-source">
<div class="__se_code_view language-javascript">&lt;!DOCTYPE html&gt;
&lt;html&gt;
  &lt;head&gt;
    &lt;meta charset="utf-8"&gt;
    &lt;title&gt;RSS Feed Example with Proxy Server&lt;/title&gt;
  &lt;/head&gt;
  &lt;body&gt;
    &lt;h1&gt;RSS Feed Example with Proxy Server&lt;/h1&gt;
    &lt;div id="feed"&gt;&lt;/div&gt;
    &lt;script&gt;
      // RSS 피드 URL
      const feedUrl = "https://www.yonhapnewstv.co.kr/browse/feed/";

      // Proxy 서버 URL.
      const proxyUrl = "https://cors-anywhere.herokuapp.com/";

      // RSS 피드를 가져옵니다.
      fetch(proxyUrl + feedUrl)
        .then(response =&gt; response.text())
        .then(data =&gt; {
          // RSS 피드의 제목을 가져옵니다.
          const parser = new DOMParser();
          const xmlDoc = parser.parseFromString(data, "text/xml");
          const title = xmlDoc.getElementsByTagName("title")[0].childNodes[0].nodeValue;

          // RSS 피드의 아이템을 가져와서 HTML에 적용합니다.
          const items = xmlDoc.getElementsByTagName("item");
          let html = "&lt;h2&gt;" + title + "&lt;/h2&gt;&lt;ul&gt;";
          for (let i = 0; i &lt; items.length; i++) {
            const itemTitle = items[i].getElementsByTagName("title")[0].childNodes[0].nodeValue;
            const itemLink = items[i].getElementsByTagName("link")[0].childNodes[0].nodeValue;
            html += "&lt;li&gt;&lt;a href='" + itemLink + "'&gt;" + itemTitle + "&lt;/a&gt;&lt;/li&gt;";
          }
          html += "&lt;/ul&gt;";

          // HTML에 RSS 피드를 적용합니다.
          document.getElementById("feed").innerHTML = html;
        })
        .catch(error =&gt; console.log(error));
    &lt;/script&gt;
  &lt;/body&gt;
&lt;/html&gt;
</div>
</div>
</div>
</div>
</div>
<script class="__se_module_data" data-module='{"type":"v2_code", "id" : "SE-2267a7b3-27c8-445c-81b2-34299352792e"}' type="text/data"></script>
</div> <div class="se-component se-text se-l-default" id="SE-683c0eec-132f-4604-9375-d4def8e0e937">
<div class="se-component-content">
<div class="se-section se-section-text se-l-default">
<div class="se-module se-module-text">
<!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-101d142c-5c8f-485f-a8cd-49c6f4402770" style=""><span class="se-fs- se-ff- se-style-unset" id="SE-3e3a1924-c3d4-42af-8206-a4a924ae5583" style="color:#384248;">​</span></p><!-- } SE-TEXT --><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-9d22fde6-e88a-4ce2-84f8-0efc24c4454a" style=""><span class="se-fs- se-ff- se-style-unset" id="SE-d781656f-e5cf-40ed-ab79-3629ae384e34" style="color:#384248;background-color:#ffffff;">RSS를  그냥 가져오니 CORS에 막하는 에러가 났기 때문에 </span><span class="se-fs- se-ff- se-style-unset" id="SE-8c655b13-abc3-4bc1-8335-c100434e28be" style="color:#384248;background-color:#ffffff;"><a class="se-link" href="https://github.com/Rob--W/cors-anywhere" target="_blank">proxy</a></span><span class="se-fs- se-ff- se-style-unset" id="SE-95d882b3-3802-45d5-8f18-f23038660e93" style="color:#384248;background-color:#ffffff;">를 제공하는 서비스를 경유했습니다</span></p><!-- } SE-TEXT -->
</div>
</div>
</div>
</div> <div class="se-component se-image se-l-default" id="SE-90c55607-d68b-4e91-a934-e84a89f95953">
<div class="se-component-content se-component-content-fit">
<div class="se-section se-section-image se-l-default se-section-align-">
<div class="se-module se-module-image" style="">
<a class="se-module-image-link __se_image_link __se_link" data-linkdata='{"id" : "SE-90c55607-d68b-4e91-a934-e84a89f95953", "src" : "https://postfiles.pstatic.net/MjAyMzA0MTNfNDYg/MDAxNjgxMzc4MTI2NDE0.kwahnS8elVD1-WZN3B7ncwlabXh4xzl_ZlegNStT_J8g.Yc6-WepQrHq1uyQ_N1vv519zxspUu14Q-_LREvou8ukg.PNG.dls32208/image.png", "originalWidth" : "841", "originalHeight" : "189", "linkUse" : "false", "link" : ""}' data-linktype="img" href="#" onclick="return false;" style="">
<img alt="" class="se-image-resource" data-height="155" data-lazy-src="https://postfiles.pstatic.net/MjAyMzA0MTNfNDYg/MDAxNjgxMzc4MTI2NDE0.kwahnS8elVD1-WZN3B7ncwlabXh4xzl_ZlegNStT_J8g.Yc6-WepQrHq1uyQ_N1vv519zxspUu14Q-_LREvou8ukg.PNG.dls32208/image.png?type=w773" data-width="693" src="https://raw.githubusercontent.com/rage147-OwO/rage147-OwO.github.io/master/_images/images/2023-4-10-VRChat 에서 뉴스 보기 (RSS+github.io)/3.png">
</a>
</div>
</div>
</div>
</div>
<div class="se-component se-code se-l-default" id="SE-63e2f732-64aa-4808-9e74-641490144285">
<div class="se-component-content">
<div class="se-section se-section-code se-l-default">
<div class="se-module se-module-code se-fs-fs13">
<div class="se-code-source">
<div class="__se_code_view language-javascript">Access to fetch at 'https://www.yonhapnewstv.co.kr/browse/feed/' from origin 'null' has been blocked by CORS policy: No 'Access-Control-Allow-Origin' header is present on the requested resource. If an opaque response serves your needs, set the request's mode to 'no-cors' to fetch the resource with CORS disabled.</div>
</div>
</div>
</div>
</div>
<script class="__se_module_data" data-module='{"type":"v2_code", "id" : "SE-63e2f732-64aa-4808-9e74-641490144285"}' type="text/data"></script>
</div> <div class="se-component se-text se-l-default" id="SE-fc45908b-eae3-40d2-a228-b125970040f5">
<div class="se-component-content">
<div class="se-section se-section-text se-l-default">
<div class="se-module se-module-text">
<!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-4626015c-63b3-4498-991d-551a4231944a" style=""><span class="se-fs- se-ff-" id="SE-8542158c-77fc-4789-b2c7-01c7865d3b23" style="">​</span></p><!-- } SE-TEXT --><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-4078fcab-55b6-4fb2-810c-2d57b73293a7" style=""><span class="se-fs- se-ff-" id="SE-9b6be416-d746-4696-a08e-df24740563c4" style="">CORS(Cross-Origin Resource Sharing)는 웹 브라우저에서 보안 상의 이유로 다른 도메인의 리소스에 직접 액세스하는 것을 제한하는 정책입니다.</span></p><!-- } SE-TEXT --><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-cf4338cd-8112-4231-9814-6737ca7bffa5" style=""><span class="se-fs- se-ff-" id="SE-ea7e0f04-9e9d-4fc7-87eb-aadcd08d2b86" style="">​</span></p><!-- } SE-TEXT --><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-93b02fdb-931f-45ed-9486-780ab87e3838" style=""><span class="se-fs- se-ff-" id="SE-234c1a01-0d41-4d98-9369-0423ce07ee3f" style="">​</span></p><!-- } SE-TEXT --><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-2305358d-4a89-420d-9583-e54d48d57817" style=""><span class="se-fs- se-ff-" id="SE-181309a4-55da-4cd7-a1c8-87b1455876bc" style="">​</span></p><!-- } SE-TEXT --><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-3ddbbd6c-4b58-4b76-8cd2-2fd628a4a3d3" style=""><span class="se-fs- se-ff-" id="SE-f06af0b1-c992-4cd8-bb38-d0af96490178" style="">​</span></p><!-- } SE-TEXT -->
</div>
</div>
</div>
</div> <div class="se-component se-image se-l-default" id="SE-25cb2b0b-215d-4a60-a218-b45b5494eacc">
<div class="se-component-content se-component-content-normal">
<div class="se-section se-section-image se-l-default se-section-align-" style="max-width:519px;">
<div class="se-module se-module-image" style="">
<a class="se-module-image-link __se_image_link __se_link" data-linkdata='{"id" : "SE-25cb2b0b-215d-4a60-a218-b45b5494eacc", "src" : "https://raw.githubusercontent.com/rage147-OwO/rage147-OwO.github.io/master/_images/images/2023-4-10-VRChat 에서 뉴스 보기 (RSS+github.io)/4.png", "originalWidth" : "708", "originalHeight" : "492", "linkUse" : "false", "link" : ""}' data-linktype="img" href="#" onclick="return false;" style="">
<img alt="" class="se-image-resource" src="https://raw.githubusercontent.com/rage147-OwO/rage147-OwO.github.io/master/_images/images/2023-4-10-VRChat 에서 뉴스 보기 (RSS+github.io)/4.png"/>
</a>
</div>
</div>
</div>
</div>
<div class="se-component se-text se-l-default" id="SE-742055c0-e980-4cb0-99c8-2bb44fcdba78">
<div class="se-component-content">
<div class="se-section se-section-text se-l-default">
<div class="se-module se-module-text">
<!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-abfef0a4-5ed1-4881-a4fc-ed0a89a717df" style=""><span class="se-fs- se-ff-" id="SE-2bb39718-454b-4391-801d-cc670aca1875" style="">자바스크립트로 가져온 RSS</span></p><!-- } SE-TEXT --><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-c63a2577-bd79-483c-a8d8-a098307e6905" style=""><span class="se-fs- se-ff-" id="SE-0386b369-1b48-42f6-9f8c-f3266337c648" style="">​</span></p><!-- } SE-TEXT --><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-52414f5b-ae4a-4fd5-a3e1-67592260b021" style=""><span class="se-fs- se-ff-" id="SE-2768c96f-dd56-4f1d-be42-1c3e5e1694c1" style="">이 링크를 유니티에서 StringLoad 해보았지만...</span></p><!-- } SE-TEXT --><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-4b8143b8-a52d-40bb-9f61-e3b16c9b5ac9" style=""><span class="se-fs- se-ff-" id="SE-098210d7-444e-4188-91ea-3d7af0d29d1d" style="">​</span></p><!-- } SE-TEXT --><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-a1a9c070-b9b4-4e96-be82-079a101f4746" style=""><span class="se-fs- se-ff-" id="SE-99512a12-abdb-4437-81b7-1a9d01e5ddaf" style="">​</span></p><!-- } SE-TEXT --><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-0a8a0988-f6bc-4703-b647-12c27e42822a" style=""><span class="se-fs- se-ff-" id="SE-127e475a-a07e-4250-9e98-33246387bc23" style="">​</span></p><!-- } SE-TEXT --><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-cea49cb1-286b-4dab-8937-78721d89b5f2" style=""><span class="se-fs- se-ff-" id="SE-fd7d0de3-4e00-471e-b13d-c115d448386a" style="">​</span></p><!-- } SE-TEXT --><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-58fe5fc4-6daa-4b0f-a8ff-a97a242bc2b5" style=""><span class="se-fs- se-ff-" id="SE-6f60232a-46f9-4318-b6be-293372418c14" style="">​</span></p><!-- } SE-TEXT --><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-3e351b65-d460-4fbf-92e8-8e64abdd5c94" style=""><span class="se-fs- se-ff-" id="SE-9c8fea56-95c1-4119-8ff8-e1ddf58a6f18" style="">예상치도 못한 결과</span></p><!-- } SE-TEXT --><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-021f2130-b9f4-4164-bc7c-03639cd4092e" style=""><span class="se-fs- se-ff-" id="SE-c8aa055b-3ccf-47cf-836e-f061928b1d57" style="">​</span></p><!-- } SE-TEXT --><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-b8f96400-84e1-464d-a544-e6099584b53d" style=""><span class="se-fs- se-ff-" id="SE-9b197c25-0d14-43e3-97af-4fba6fc7c3fc" style="">유니티에서 string을 가져오니, 자바스크립트가 실행 된 결과가 아니라, 자바스크립트 코드 자체를 가져왔다 ㅋㅋ</span></p><!-- } SE-TEXT -->
</div>
</div>
</div>
</div> <div class="se-component se-image se-l-default" id="SE-57f24b10-17c2-4d89-a17b-94971e3716fa">
<div class="se-component-content se-component-content-fit">
<div class="se-section se-section-image se-l-default se-section-align-">
<div class="se-module se-module-image" style="">
<a class="se-module-image-link __se_image_link __se_link" data-linkdata='{"id" : "SE-57f24b10-17c2-4d89-a17b-94971e3716fa", "src" : "https://raw.githubusercontent.com/rage147-OwO/rage147-OwO.github.io/master/_images/images/2023-4-10-VRChat 에서 뉴스 보기 (RSS+github.io)/5.png", "originalWidth" : "1284", "originalHeight" : "868", "linkUse" : "false", "link" : ""}' data-linktype="img" href="#" onclick="return false;" style="">
<img alt="" class="se-image-resource" src="https://raw.githubusercontent.com/rage147-OwO/rage147-OwO.github.io/master/_images/images/2023-4-10-VRChat 에서 뉴스 보기 (RSS+github.io)/5.png"/>
</a>
</div>
</div>
</div>
</div>
<div class="se-component se-text se-l-default" id="SE-3540d163-b736-4d50-a551-104c171cb113">
<div class="se-component-content">
<div class="se-section se-section-text se-l-default">
<div class="se-module se-module-text">
<!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-a34c5197-1216-4ad8-a069-542c9586ef11" style=""><span class="se-fs- se-ff-" id="SE-5c0fa930-8d32-476d-8521-377ab9a41e31" style="">당연히 페이지 자체를 가져오니 자바스크립트를 가져오는구나... ㅋㅋ</span></p><!-- } SE-TEXT --><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-f6313aef-e880-4500-b628-683e97ed83b1" style=""><span class="se-fs- se-ff-" id="SE-86a93e6d-f619-4226-9567-7c10525db3c9" style="">쓸데없이 html 난독화를 찾아본건 덤</span></p><!-- } SE-TEXT --><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-8e07a996-b803-4661-8c2d-f49e06b8abb6" style=""><span class="se-fs- se-ff-" id="SE-cad87e89-74c8-423d-a74e-802362d9e33c" style="">​</span></p><!-- } SE-TEXT --><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-9839fdb0-47db-4cf9-afea-85331646e31f" style=""><span class="se-fs- se-ff-" id="SE-c591404f-4199-4de8-8645-f7bee8c62027" style="">​</span></p><!-- } SE-TEXT --><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-252ba7fa-0a19-401f-809b-077d20351f41" style=""><span class="se-fs- se-ff-" id="SE-8ba7caa0-a598-4875-bec8-b80a7f7ca194" style="">​</span></p><!-- } SE-TEXT --><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-44174d3f-4f29-4ca1-9d8a-298b55dac7f5" style=""><span class="se-fs- se-ff-" id="SE-52f07069-371d-4c64-8e69-5aebb0efbd2d" style="">뉴스를 수정하려면 계속 커밋을 해야 하는데, 컴퓨터를 항상 킬 수는 없으니, 클라우드 컴퓨팅을 이용하기로 했다.</span></p><!-- } SE-TEXT --><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-79b01719-0e5d-4a27-a2a0-5feb8081781d" style=""><span class="se-fs- se-ff-" id="SE-45a33f98-ea33-4727-94f9-4d84b7fdff10" style="">​</span></p><!-- } SE-TEXT --><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-6ab31048-6904-4601-a8ef-964136709db7" style=""><span class="se-fs- se-ff-" id="SE-70c16bad-2676-478d-9aa4-e226f5c295de" style="">옛날에 만들어놓은 계정이 있으나, 현재 프리티어 혜택이 적용이 안되는 것으로 알고있다</span></p><!-- } SE-TEXT --><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-7a260648-5760-43bc-aeaf-92cc686fbe88" style=""><span class="se-fs- se-ff-" id="SE-29e81488-b767-4aea-9241-bf852723bc76" style="">그렇기에 계정을 새로 판 후 VM을 생성했다.</span></p><!-- } SE-TEXT -->
</div>
</div>
</div>
</div> <div class="se-component se-image se-l-default" id="SE-846c4737-4448-4460-b943-859725585e77">
<div class="se-component-content se-component-content-fit">
<div class="se-section se-section-image se-l-default se-section-align-">
<div class="se-module se-module-image" style="">
<a class="se-module-image-link __se_image_link __se_link" data-linkdata='{"id" : "SE-846c4737-4448-4460-b943-859725585e77", "src" : "https://postfiles.pstatic.net/MjAyMzA0MTFfMTE5/MDAxNjgxMTM4ODcxNDAw.Sxf_Vd8J04SYL-UcCO9ZUGeFXZQE62LvQCFc4hWO6Swg.i1eunE1G--Ib4JHrkFXh8jqAK50MeKjPjohqid21Vmkg.PNG.dls32208/image.png", "originalWidth" : "939", "originalHeight" : "600", "linkUse" : "false", "link" : ""}' data-linktype="img" href="#" onclick="return false;" style="">
<img alt="" class="se-image-resource" data-height="442" data-lazy-src="https://postfiles.pstatic.net/MjAyMzA0MTFfMTE5/MDAxNjgxMTM4ODcxNDAw.Sxf_Vd8J04SYL-UcCO9ZUGeFXZQE62LvQCFc4hWO6Swg.i1eunE1G--Ib4JHrkFXh8jqAK50MeKjPjohqid21Vmkg.PNG.dls32208/image.png?type=w773" data-width="693" src="https://raw.githubusercontent.com/rage147-OwO/rage147-OwO.github.io/master/_images/images/2023-4-10-VRChat 에서 뉴스 보기 (RSS+github.io)/6.png"/>
</a>
</div>
</div>
</div>
</div>
<div class="se-component se-text se-l-default" id="SE-3a137bd7-0b05-4a41-af1f-a8d1e636e7d9">
<div class="se-component-content">
<div class="se-section se-section-text se-l-default">
<div class="se-module se-module-text">
<!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-97ab8ee8-4957-4b4f-9da5-087c72faae83" style=""><span class="se-fs- se-ff-" id="SE-33373deb-44d1-481c-a557-b2baf9d31ecc" style=""><a class="se-link" href="https://cloud.google.com/free/docs/free-cloud-features?hl=ko#compute" target="_blank">무료로 사용이 가능한 조건</a></span><span class="se-fs- se-ff-" id="SE-7b565330-6202-43dd-9e13-1eaf168dbbc3" style="">:</span></p><!-- } SE-TEXT --><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-7588e4f2-818e-456d-9a22-bdf1568c4aa7" style=""><span class="se-fs- se-ff-" id="SE-5f17e302-dbd8-49e3-ba0f-048715040c6e" style="">e2-micro</span></p><!-- } SE-TEXT --><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-07564971-afcb-4e9e-969f-bc63d848f494" style=""><span class="se-fs- se-ff-" id="SE-c2f23eb6-7b83-4924-8de9-a1fdaccf0293" style="">지역 제한</span></p><!-- } SE-TEXT --><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-36a8ed6f-0101-4614-a0ac-e8a3823512d8" style=""><span class="se-fs- se-ff-" id="SE-0450d725-0a2c-4818-832c-28e947706e04" style="">30GB/월 표준 디스크</span></p><!-- } SE-TEXT --><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-62b983d6-bc37-4f13-89ca-dc50b80a90aa" style=""><span class="se-fs- se-ff-" id="SE-884baaf7-786e-4507-a55b-3568d11e8f2b" style="">​</span></p><!-- } SE-TEXT --><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-3c540b67-be44-4719-ab97-7dbe7187b040" style=""><span class="se-fs- se-ff-" id="SE-447025c1-6e2a-4147-a96b-45c4b5c91d4e" style="">​</span></p><!-- } SE-TEXT --><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-04f574eb-dbc0-494d-bec2-6562493ef1f4" style=""><span class="se-fs- se-ff-" id="SE-2b281b9b-d429-4df5-8eae-9a1e6ba4e1d6" style="">​</span></p><!-- } SE-TEXT --><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-4e29a482-cf69-475d-b51a-759a224643e2" style=""><span class="se-fs- se-ff-" id="SE-1b2b1d81-622f-43ab-8aa5-5e4d542b8b72" style="">​</span></p><!-- } SE-TEXT --><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-ff181699-6b0d-4cae-aac8-c1b1425942e4" style=""><span class="se-fs- se-ff-" id="SE-17c4e797-cde0-4c73-8bb8-469fa4d8775b" style="">​</span></p><!-- } SE-TEXT --><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-c3b2aab3-3d15-42a2-a5fb-b6b32c734470" style=""><span class="se-fs- se-ff-" id="SE-dc3a0a3e-a0be-4a79-bb1c-8b1525001d6a" style="">​</span></p><!-- } SE-TEXT --><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-45411ec9-1a68-4691-a0e9-56f113ccf4e3" style=""><span class="se-fs- se-ff-" id="SE-48d08285-5d6c-4b80-8914-cc0e045badf4" style="">​</span></p><!-- } SE-TEXT --><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-b3a6b913-c512-4872-b6b2-b429393d9092" style=""><span class="se-fs- se-ff-" id="SE-ef5d6f4a-8de2-4cab-8136-70c3ee1ec8e4" style="">​</span></p><!-- } SE-TEXT --><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-3f03e814-51ad-482f-8567-6b545d556822" style=""><span class="se-fs- se-ff-" id="SE-1e3b06c5-debe-496c-bf58-b2d895bc9b0d" style="">​</span></p><!-- } SE-TEXT -->
</div>
</div>
</div>
</div> <div class="se-component se-quotation se-l-quotation_line" id="SE-3139b846-6efb-4a67-8e61-1c00b6711896">
<div class="se-component-content">
<div class="se-section se-section-quotation se-l-quotation_line">
<blockquote class="se-quotation-container">
<div class="se-module se-module-text se-quote"><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-24a751c9-742d-4b16-9f51-c605d8116ce1" style=""><span class="se-fs- se-ff-" id="SE-c52d2ba0-4127-48f7-a266-3386294e28f7" style="">깃허브 리포지토리 SSH 연결</span></p><!-- } SE-TEXT --></div>
<div class="se-module se-module-text se-cite"><p class="se-text-paragraph se-text-paragraph-align-" id="SE-bbf841e7-6a03-40e8-9be2-df58aa088620" style=""><span class="se-fs- se-ff-" id="SE-455e3c84-11ec-4909-b0f3-9c71cc9c3eb3" style="">우분투에서 SSH키 연결하기</span></p></div>
</blockquote>
</div>
</div>
</div>
<div class="se-component se-text se-l-default" id="SE-e0c84484-6992-4a4c-9fae-a7a61a0402fd">
<div class="se-component-content">
<div class="se-section se-section-text se-l-default">
<div class="se-module se-module-text">
<!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-002e9de4-73de-475b-98cb-002fe4ddae27" style=""><span class="se-fs- se-ff-" id="SE-5af4160f-c18e-4ca4-8467-1fe35dffd5a7" style="">깃허브 리포지토리는 SSH(Secure Shell)사용이 가능하기 때문에, 키를 등록해놓으면 따로 아이디와 패스워드를 이용해 연결하지 않아도 된다.</span></p><p class="se-text-paragraph se-text-paragraph-align-" id="SE-a4d031d8-c6d8-4ff8-9082-5acbaeb81e95" style=""><span class="se-fs- se-ff-" id="SE-e7e3b0f5-df54-4f5d-9ae8-4332aa6e9c86" style="">​</span></p><p class="se-text-paragraph se-text-paragraph-align-" id="SE-d2d2e388-3fe5-4951-9292-c761e1b7fb96" style=""><span class="se-fs- se-ff-" id="SE-fff0eed8-5662-430e-a1aa-f733080eaf84" style="">연결은 클라이언트에서 키(공개키)를 생성후, 깃허브 리포지토리에서 등록 하면 된다.</span></p><p class="se-text-paragraph se-text-paragraph-align-" id="SE-d156dee3-9b2e-4e98-9db6-4afc804d6684" style=""><span class="se-fs- se-ff-" id="SE-d2412de2-2e70-4730-8f2d-d687df66f4bd" style="">​</span></p><p class="se-text-paragraph se-text-paragraph-align-" id="SE-8d7b723d-45b9-4152-97d8-8b43056e3c5f" style=""><span class="se-fs- se-ff-" id="SE-611b8221-6efd-4630-afda-36fada217d81" style="">우분투에서 githubSSH를 연결하는 방법은</span></p><p class="se-text-paragraph se-text-paragraph-align-" id="SE-1f2f8e55-3804-4c26-9079-7e4d29b17a02" style=""><span class="se-fs- se-ff-" id="SE-5164fe70-98c9-43d3-980b-c6fbcb07ab69" style="">​</span></p><ol class="se-text-list se-text-list-type-decimal"><li class="se-text-list-item"><p class="se-text-paragraph se-text-paragraph-align-" id="SE-8ad1d8e7-8dd0-4cc2-951a-e58ba4d80222" style=""><span class="se-fs- se-ff-" id="SE-15336b31-a908-4968-aca1-e24869ad2b27" style="">클라이언트에서 SSH키를 생성한다</span></p></li></ol><p class="se-text-paragraph se-text-paragraph-align-" id="SE-b33586c0-3b85-4388-a3f4-9359c106535e" style=""><span class="se-fs- se-ff-" id="SE-d7c37adb-a3f9-4d2e-b344-40ce001a15d6" style="">ssh-keygen -t rsa -b 4096 -C "github@example.com"</span></p><p class="se-text-paragraph se-text-paragraph-align-" id="SE-343ddf03-7c23-4df9-a4a0-781f64b7498d" style=""><span class="se-fs- se-ff-" id="SE-96644b40-ed87-4b7d-b76a-dc7e61e223dc" style="">​</span></p><p class="se-text-paragraph se-text-paragraph-align-" id="SE-3c3c0c9b-5e95-4980-af72-fd4b0b97aab9" style=""><span class="se-fs- se-ff-" id="SE-25a92f00-38bf-4bc2-919d-04229b9f3f84" style="">ssh-keygen으로 SSH키를 생성 할 수 있다.</span></p><p class="se-text-paragraph se-text-paragraph-align-" id="SE-740d550e-2640-468f-95b5-2966828c4445" style=""><span class="se-fs- se-ff-" id="SE-259c8e02-e1e5-47bf-85a0-4d4d49ba375d" style="">​</span></p><p class="se-text-paragraph se-text-paragraph-align-" id="SE-906ef406-30ad-4ca7-8bf6-7aaaaec1beae" style=""><span class="se-fs- se-ff-" id="SE-86a146b9-6521-4695-a847-bde52c953474" style="">2. SSH 키를 복사하기</span></p><p class="se-text-paragraph se-text-paragraph-align-" id="SE-33fd1659-f14e-401e-9fdc-3e551a2169de" style=""><span class="se-fs- se-ff-" id="SE-aa931efe-5c99-4334-bf5b-5f432dc98b62" style="">cat ~/.ssh/id_rsa.pub</span></p><p class="se-text-paragraph se-text-paragraph-align-" id="SE-3f229fa0-a84b-4fcc-bd13-d8ca32f83b93" style=""><span class="se-fs- se-ff-" id="SE-8bf994c1-b2b0-4a4d-b090-a7cf3ca8e77f" style="">​</span></p><p class="se-text-paragraph se-text-paragraph-align-" id="SE-d28f84ed-964e-495b-86d8-1d6d69a4bf7a" style=""><span class="se-fs- se-ff-" id="SE-51e33f4d-3e0e-410a-bb20-d79e81e3117a" style="">3. GIthub 리포지토리에서 SSH 키 생성하기</span></p><p class="se-text-paragraph se-text-paragraph-align-" id="SE-b3c5d6da-382b-4e29-af3e-2f8c698a5621" style=""><span class="se-fs- se-ff-" id="SE-6cdc5bdc-d78c-4fe5-9c2b-9ae0db4d7bb4" style="">​</span></p><p class="se-text-paragraph se-text-paragraph-align-" id="SE-2f3e359b-bf1a-40a6-a041-e2b90e9fff62" style=""><span class="se-fs- se-ff-" id="SE-14385ce3-b276-45ca-965e-2d35331abb78" style="">세팅의 Deploy Key를 등록하면 된다.</span></p><!-- } SE-TEXT -->
</div>
</div>
</div>
</div> <div class="se-component se-image se-l-default" id="SE-576c4d8d-d192-4e64-b372-cf4737f7edf2">
<div class="se-component-content se-component-content-fit">
<div class="se-section se-section-image se-l-default se-section-align-">
<div class="se-module se-module-image" style="">
<a class="se-module-image-link __se_image_link __se_link" data-linkdata='{"id" : "SE-576c4d8d-d192-4e64-b372-cf4737f7edf2", "src" : "https://postfiles.pstatic.net/MjAyMzA0MTFfMjAx/MDAxNjgxMTM5MjQ3Njk1.OHO0v2KDUYH9S5nXoEk_woS-xKZgC39UBf9Px_fQEjAg.oz8KL7YevVg3gczVP_X98wKKOdQ-uVdFZ_M1iTZqk64g.PNG.dls32208/image.png", "originalWidth" : "1292", "originalHeight" : "646", "linkUse" : "false", "link" : ""}' data-linktype="img" href="#" onclick="return false;" style="">
<img alt="" class="se-image-resource" data-height="346" data-lazy-src="https://postfiles.pstatic.net/MjAyMzA0MTFfMjAx/MDAxNjgxMTM5MjQ3Njk1.OHO0v2KDUYH9S5nXoEk_woS-xKZgC39UBf9Px_fQEjAg.oz8KL7YevVg3gczVP_X98wKKOdQ-uVdFZ_M1iTZqk64g.PNG.dls32208/image.png?type=w773" data-width="693" src="https://raw.githubusercontent.com/rage147-OwO/rage147-OwO.github.io/master/_images/images/2023-4-10-VRChat 에서 뉴스 보기 (RSS+github.io)/7.png"/>
</a>
</div>
</div>
</div>
</div>
<div class="se-component se-text se-l-default" id="SE-0b37849f-e535-4282-bd33-8d609381cea0">
<div class="se-component-content">
<div class="se-section se-section-text se-l-default">
<div class="se-module se-module-text">
<!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-0fd02d26-458b-4177-89db-ab55611ab231" style=""><span class="se-fs- se-ff-" id="SE-167d26d2-6242-4ee7-aba6-c414c2a5d3f2" style="">​</span></p><!-- } SE-TEXT --><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-034694c5-7241-422b-9b50-82a9f3466889" style=""><span class="se-fs- se-ff-" id="SE-7aa18fdc-10dc-410f-9c4d-704ae9be04ce" style="">​</span></p><!-- } SE-TEXT --><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-fe5958aa-986c-447a-bc18-1b65a325df99" style=""><span class="se-fs- se-ff-" id="SE-3c6f3fb2-e609-467c-9eb5-5c940509beaa" style="">여기서 필자는 서버에서의 커밋 기록이 Github Contributors에 남기고 싶지 않아서 부계정을 이용했다.</span></p><!-- } SE-TEXT --><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-7ff6322a-a2c3-487c-ae75-b2869887d7d6" style=""><span class="se-fs- se-ff-" id="SE-cab8be94-039b-421f-a72a-f261a05e8e51" style=""> 깃허브 리포지토리를 부계정으로 옮긴 뒤 SSH키를 등록한 후 다시 본계정으로 소유권을 옮기면 SSH로 커밋을 해도 키를 만든 부계정 이름으로 커밋된다.</span></p><!-- } SE-TEXT --><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-0fcfc37c-7ebf-4783-acba-3b9a611d423e" style=""><span class="se-fs- se-ff-" id="SE-05d3feaf-3116-46e6-86d7-9779bfdb6b3c" style="">​</span></p><!-- } SE-TEXT --><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-949f5dec-3802-4be3-9a3b-7186779ac7ea" style=""><span class="se-fs- se-ff-" id="SE-d15eea3b-43b4-4ed5-b205-643b1ef4d2f9" style="">하루도 빠짐없이 48개를 커밋하는 사람이 있다고 하면 무섭지 않은가...</span></p><!-- } SE-TEXT --><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-e4084471-bfa4-45bf-b9c2-900d86a9d346" style=""><span class="se-fs- se-ff-" id="SE-1642873b-8847-4ecf-829b-60ed7dad64a4" style="">​</span></p><!-- } SE-TEXT --><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-d6ed9ca3-4346-4938-a25d-27b1948cc9c2" style=""><span class="se-fs- se-ff-" id="SE-7eafde70-baa2-4e16-9f77-71486970b4ae" style="">​</span></p><!-- } SE-TEXT --><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-b1334e54-2807-4a27-a7fa-741e91f50134" style=""><span class="se-fs- se-ff-" id="SE-7015add4-c090-4ec0-8d6b-ecc363bd6c34" style="">​</span></p><!-- } SE-TEXT --><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-eefdf70a-f02c-4647-aa31-30e9bdece24c" style=""><span class="se-fs- se-ff-" id="SE-c534d79a-42e9-4eb6-babe-674981bab737" style="">​</span></p><!-- } SE-TEXT --><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-b9ec0079-8320-459e-ab5c-c9201fe73048" style=""><span class="se-fs- se-ff-" id="SE-0ea6a8d9-1188-4a24-bbcd-c7107d41a180" style="">​</span></p><!-- } SE-TEXT --><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-6d8eb449-967f-4371-b84d-623017b801a3" style=""><span class="se-fs- se-ff-" id="SE-60812c3b-fabf-4458-99a6-dd40df9afe5b" style="">​</span></p><!-- } SE-TEXT -->
</div>
</div>
</div>
</div> <div class="se-component se-quotation se-l-quotation_line" id="SE-fe6e8e74-1ca4-418a-9132-26ec9f46046f">
<div class="se-component-content">
<div class="se-section se-section-quotation se-l-quotation_line">
<blockquote class="se-quotation-container">
<div class="se-module se-module-text se-quote"><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-a520472e-6bda-4ec9-a38d-d5dbea36d4cc" style=""><span class="se-fs- se-ff-" id="SE-bc1e2b20-8e52-4f1f-92c0-d4cc0295ff67" style="">RSS를 받아서 언론사.HTML로 저장한 후 커밋하는 코드 작성</span></p><!-- } SE-TEXT --></div>
</blockquote>
</div>
</div>
</div>
<div class="se-component se-text se-l-default" id="SE-aa869e41-2003-45a7-a38b-c0da4e8db878">
<div class="se-component-content">
<div class="se-section se-section-text se-l-default">
<div class="se-module se-module-text">
<!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-0ed0bf43-7b8b-40f6-8031-2f323cfbdb35" style=""><span class="se-fs- se-ff-" id="SE-2049cdbd-5356-4683-8e4c-3608083a9366" style="">다음은 코드 작성이다.</span></p><!-- } SE-TEXT --><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-3dcf1ad3-815f-4a2c-a2d0-a1b376fb1a1a" style=""><span class="se-fs- se-ff-" id="SE-f1db0827-1dc5-4ad8-a59f-4967de1f6c5e" style="">​</span></p><!-- } SE-TEXT --><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-6a790a09-a245-4362-be42-0a41710102db" style=""><span class="se-fs- se-ff-" id="SE-21a378d8-daab-4094-8058-acebadd58b82" style="">기능은 RSS를 받아 언론사이름.HTML로 저장하는 기능이다.</span></p><!-- } SE-TEXT --><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-3a6d40bd-b10b-43ea-a6f6-bf3ca6703fe6" style=""><span class="se-fs- se-ff-" id="SE-fffb4dd4-4412-44d5-95b9-7bf8b0cb3bdf" style="">​</span></p><!-- } SE-TEXT --><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-0c9859bc-d574-49d7-8247-3abde6d36ce8" style=""><span class="se-fs- se-ff-" id="SE-873c30af-1a60-41eb-8531-88530f2a61c0" style="">파이썬은 라이브러리들이 편하게 되어있기에 RSS를 가져와주는 feedparser를 사용했다.</span></p><!-- } SE-TEXT --><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-10c65d5d-043d-4bd4-8d52-ebf0d803a33d" style=""><span class="se-fs- se-ff-" id="SE-1a23c3b5-e965-46e4-a812-f0ca0e66c6ec" style="">​</span></p><!-- } SE-TEXT --><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-bd91f6ba-fdd6-4b55-8c67-28a62cb95cff" style=""><span class="se-fs- se-ff-" id="SE-0ef84590-75ba-4156-a078-8f0abc26ad8a" style="">Feedparser는 RSS뿐만이 아니라 Atom, RDF같은 웹 피드 형식을 파싱 가능하다.</span></p><!-- } SE-TEXT --><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-9a84df41-a5a2-4c4d-b00b-d4a4ea885a29" style=""><span class="se-fs- se-ff-" id="SE-138820d6-2691-4582-bfab-92a3fe639896" style="">​</span></p><!-- } SE-TEXT --><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-d3bd759d-0d56-4db0-b721-7d14b1aa8e69" style=""><span class="se-fs- se-ff-" id="SE-408e090e-630f-4e37-965a-c8e68bde97b3" style="">Feedparser에는 title, link, published, summary가 포함된다.</span></p><!-- } SE-TEXT --><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-970586d2-c7e5-4ddb-9495-cbf1a83635c2" style=""><span class="se-fs- se-ff-" id="SE-3cb6645f-ecfc-49a7-a0b5-d1ac78e9037a" style="">​</span></p><!-- } SE-TEXT --><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-1d1ccf0e-f465-4015-a59e-41600b787c50" style=""><span class="se-fs- se-ff-" id="SE-74b453f7-355d-47c4-8a28-e69cd4a2926d" style="">필자가 쓸 것은 title과 기사의 내용.</span></p><!-- } SE-TEXT --><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-af4266f3-3e01-4d31-9686-0aaf2549cb21" style=""><span class="se-fs- se-ff-" id="SE-d3e148d6-04c8-4d24-b31a-a52aa9607a5c" style="">​</span></p><!-- } SE-TEXT --><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-8c12b448-9a50-40f1-9e5e-8c02058f7aff" style=""><span class="se-fs- se-ff-" id="SE-e4b771b8-26d0-422b-a57a-9d5c919a1719" style="">기사의 내용은 content, summary, description 등이 있는데, 이는 언론사 RSS 피드의 형식에 따라 다르다. 그렇기에 세개를 모두 받아온 뒤 가장 긴 내용을 사용하기로 했다.</span></p><!-- } SE-TEXT --><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-7bf55231-422c-4295-98c1-0d8702450850" style=""><span class="se-fs- se-ff-" id="SE-c90d3c2c-9e46-40a3-9f46-b0cf77c28870" style="">​</span></p><!-- } SE-TEXT --><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-2ca8d4d0-35d2-4ac0-b7f4-aaf3a07c74d6" style=""><span class="se-fs- se-ff-" id="SE-6d9bbef5-0e41-4941-bfcb-81affcb2bff3" style="">내용에서는 html태그와 쓸모 없는 괄호들도 포함되기에 길이를 비교하기 전 꼭 제거해야 한다.</span></p><!-- } SE-TEXT --><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-82de098f-750d-4754-90c8-49363cfa59f0" style=""><span class="se-fs- se-ff-" id="SE-6c34fb58-b039-470a-8a71-74867f324432" style="">​</span></p><!-- } SE-TEXT --><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-023da7e8-929e-4109-aa50-cdd1e2fd20ea" style=""><span class="se-fs- se-ff-" id="SE-f1dc941b-d8ea-4c26-ae19-e74206e5af09" style="">그리고 기사에는 잘 쓰이지 않는 특수문자를 이용하여 ^은 테마, _로는 각 기사들을 구분했다. 특수문자로 나눈 이유는 유니티에서 string을 사용하는 특성상 가비지가 쌓이기 때문에, 특히 VR을 사용하는 환경에서는 영향이 있다. 그렇기에 char split으로 나눌 수 있는 특수문자를 사용했다.</span></p><!-- } SE-TEXT --><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-0fb1dd62-5668-48c3-bf4e-8411bcf94aeb" style=""><span class="se-fs- se-ff-" id="SE-53f3b37d-9182-4861-b91b-0eccb90a22bc" style="">​</span></p><!-- } SE-TEXT --><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-f8dbb489-7d2b-49ea-8154-e4bebb179d3b" style=""><span class="se-fs- se-ff-" id="SE-c192fc8e-2077-401c-992f-eb2564f38016" style="">그리고서 while과 sleep으로 일정 시간마다 반복되게끔 해두었다.</span></p><!-- } SE-TEXT -->
</div>
</div>
</div>
</div> <div class="se-component se-code se-l-code_black" id="SE-5ed30cf0-8fcd-43ac-9cd0-859f72c04d90">
<div class="se-component-content">
<div class="se-section se-section-code se-l-code_black">
<div class="se-module se-module-code se-fs-fs13">
<div class="se-code-source">
<div class="__se_code_view language-javascript">import feedparser
import subprocess
import os
import time
from bs4 import BeautifulSoup
import time

def remove_parenthesis(string):
    # 주어진 문자열에서 괄호로 시작하는 부분을 찾아 삭제
    while True:
        start_index = string.find("{")
        end_index = string.find("}")
        if(end_index-start_index&lt;1000):
            if start_index != -1 and end_index != -1:
                string = string[:start_index] + string[end_index+1:]
            else:
                break
    # 삭제된 문자열 반환
    return string


def remove_p_and_img_tags(html_text):
    html_text = str(html_text)
    soup = BeautifulSoup(html_text, 'html.parser')
    for tag in soup(['p', 'img']):
        tag.decompose()
    return remove_parenthesis(str(soup))








# ssh-agent 실행
ssh_agent = subprocess.Popen(['ssh-agent', '-s'], stdout=subprocess.PIPE)
# ssh-add 실행
subprocess.call('ssh-add ~/.ssh/id_rsa', shell=True)
# RSS 피드 URL 설정

rss_url = "http://www.yonhapnewstv.co.kr/browse/feed/"
# feedparser로 RSS 뉴스 기사 파싱
feed = feedparser.parse(rss_url)

# 저장할 파일 경로와 파일명 설정
base_path = "/home/dls32208/Documents/VRChatKoreaNews"
file_name = "news.html"


rss_urls = {
    '조선일보': {
        '전체기사': 'https://www.chosun.com/arc/outboundfeeds/rss/?outputType=xml',
        '정치': 'https://www.chosun.com/arc/outboundfeeds/rss/category/politics/?outputType=xml',
        '경제': 'https://www.chosun.com/arc/outboundfeeds/rss/category/economy/?outputType=xml',
        '사회': 'https://www.chosun.com/arc/outboundfeeds/rss/category/national/?outputType=xml',
        '국제': 'https://www.chosun.com/arc/outboundfeeds/rss/category/international/?outputType=xml',
        '문화라이프': 'https://www.chosun.com/arc/outboundfeeds/rss/category/culture-life/?outputType=xml',
        '오피니언': 'https://www.chosun.com/arc/outboundfeeds/rss/category/opinion/?outputType=xml',
        '스포츠': 'https://www.chosun.com/arc/outboundfeeds/rss/category/sports/?outputType=xml',
        '연예': 'https://www.chosun.com/arc/outboundfeeds/rss/category/entertainments/?outputType=xml'
    },
    '동아일보': {
        '전체기사': 'https://rss.donga.com/total.xml',
        '정치': 'https://rss.donga.com/politics.xml',
        '사회': 'https://rss.donga.com/national.xml',
        '경제': 'https://rss.donga.com/economy.xml',
        '국제': 'https://rss.donga.com/international.xml',
        '사설칼럼': 'https://rss.donga.com/editorials.xml',
        '의학과학': 'https://rss.donga.com/science.xml',
        '문화연예': 'https://rss.donga.com/culture.xml',
        '스포츠': 'https://rss.donga.com/sports.xml',
        '사람속으로': 'https://rss.donga.com/inmul.xml',
        '건강': 'https://rss.donga.com/health.xml',
        '레져': 'https://rss.donga.com/leisure.xml',
        '도서': 'https://rss.donga.com/book.xml',
        '공연': 'https://rss.donga.com/show.xml',
        '여성': 'https://rss.donga.com/woman.xml',
        '여행': 'https://rss.donga.com/travel.xml',
        '생활정보': 'https://rss.donga.com/lifeinfo.xml',
        '스포츠': 'https://rss.donga.com/sportsdonga/sports.xml',
        '야구MLB': 'https://rss.donga.com/sportsdonga/baseball.xml',
        '축구': 'https://rss.donga.com/sportsdonga/soccer.xml',
        '골프': 'https://rss.donga.com/sportsdonga/golf.xml',
        '일반': 'https://rss.donga.com/sportsdonga/sports_general.xml',
        'e스포츠': 'https://rss.donga.com/sportsdonga/sports_game.xml',
        '엔터테인먼트': 'https://rss.donga.com/sportsdonga/entertainment.xml',
    },
    '매일경제': {
        '헤드라인': 'https://www.mk.co.kr/rss/30000001/',
        '전체뉴스': 'https://www.mk.co.kr/rss/40300001/',
        '경제': 'https://www.mk.co.kr/rss/30100041/',
        '정치': 'https://www.mk.co.kr/rss/30200030/',
        '사회': 'https://www.mk.co.kr/rss/50400012/',
        '국제': 'https://www.mk.co.kr/rss/30300018/',
        '기업경영': 'https://www.mk.co.kr/rss/50100032/',
        '증권': 'https://www.mk.co.kr/rss/50200011/',
        '부동산': 'https://www.mk.co.kr/rss/50300009/',
        '문화연예': 'https://www.mk.co.kr/rss/30000023/',
        '스포츠': 'https://www.mk.co.kr/rss/71000001/',
        '게임': 'https://www.mk.co.kr/rss/50700001/',
        'MBA': 'https://www.mk.co.kr/rss/40200124/',
        '머니앤리치스': 'https://www.mk.co.kr/rss/40200003/',
        'English': 'https://www.mk.co.kr/rss/30800011/',
        '이코노미': 'https://www.mk.co.kr/rss/50000001/',
        '시티라이프': 'https://www.mk.co.kr/rss/60000007/'
    }
}
</div>
</div>
</div>
</div>
</div>
<script class="__se_module_data" data-module='{"type":"v2_code", "id" : "SE-5ed30cf0-8fcd-43ac-9cd0-859f72c04d90"}' type="text/data"></script>
</div> <div class="se-component se-code se-l-code_black" id="SE-eaefcfed-0508-44b9-ac62-b1fada0a4b20">
<div class="se-component-content">
<div class="se-section se-section-code se-l-code_black">
<div class="se-module se-module-code se-fs-fs13">
<div class="se-code-source">
<div class="__se_code_view language-javascript">while True:
    for press in rss_urls:
        file_name = f"{press}.html"
        file_path = os.path.join(base_path, file_name)
        press_html = ""
        titleList=""
        for category in rss_urls[press]:
            rss_url = rss_urls[press][category]
            # feedparser로 RSS 뉴스 기사 파싱
            feed = feedparser.parse(rss_url)
            # 기사 정보를 HTML 코드로 변환하여 press_html에 추가
            titleList=titleList+category+"_"
            for entry in feed.entries:
                temp = f"_{entry.title}\n"
                try:
                    if len(remove_p_and_img_tags(entry.content[0])) &gt; len(remove_p_and_img_tags(entry.description)) and len(remove_p_and_img_tags(entry.content[0])) &gt; len(remove_p_and_img_tags(entry.summary)):
                        if len(remove_p_and_img_tags(entry.content[0])) &lt;2:
                            continue
                        temp += f"{remove_p_and_img_tags(entry.content[0])}\n\n"
                    else:
                        if len(remove_p_and_img_tags(entry.summary)) &lt; 2:
                            continue
                        temp += f"{remove_p_and_img_tags(entry.summary)}\n\n"
                except AttributeError:
                    if len(remove_p_and_img_tags(entry.description)) &lt; 2:
                        continue
                    temp +=f"{remove_p_and_img_tags(entry.description)}\n\n"
                press_html = press_html+temp
            press_html +="^"; 

        press_html=titleList+'\n'+press_html

        # HTML 파일 생성
        with open(file_path, "w") as f:
            f.write("&lt;html&gt;\n&lt;head&gt;\n&lt;title&gt;News&lt;/title&gt;\n&lt;/head&gt;\n&lt;body&gt;\n")
            f.write(press_html)
            f.write("&lt;/body&gt;\n&lt;/html&gt;")

        # 각 언론사별로 commit 및 push
        subprocess.call(f"git add {file_path}", cwd=base_path, shell=True)
        subprocess.call(f"git commit -m 'Update news' &amp;&amp; git push", cwd=base_path, shell=True)

    # 1분 대기
    time.sleep(1800)</div>
</div>
</div>
</div>
</div>
<script class="__se_module_data" data-module='{"type":"v2_code", "id" : "SE-eaefcfed-0508-44b9-ac62-b1fada0a4b20"}' type="text/data"></script>
</div> <div class="se-component se-text se-l-default" id="SE-f6a16e89-7953-4bb1-8217-4053a854f2e0">
<div class="se-component-content">
<div class="se-section se-section-text se-l-default">
<div class="se-module se-module-text">
<!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-f6a6456f-62c3-4181-bd6a-b1580730048c" style=""><span class="se-fs- se-ff-" id="SE-83d2dbef-ba1a-4fbe-a4a0-9b9ba1bb610b" style="">​</span></p><!-- } SE-TEXT --><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-30603b40-e65b-4633-9caf-a2c335e83f53" style=""><span class="se-fs- se-ff-" id="SE-a41fdbc6-352f-4769-a77e-c8e0498725da" style="">​</span></p><!-- } SE-TEXT --><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-57985f6f-ac51-4abe-813e-899b3434de3f" style=""><span class="se-fs- se-ff-" id="SE-6a9a630a-1a91-4404-b657-cf2805cb6515" style="">​</span></p><!-- } SE-TEXT --><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-fc2c87d7-ed4c-47c1-8a12-dea4ade9338a" style=""><span class="se-fs- se-ff-" id="SE-7ab3ac47-c823-4659-bd7b-3eb52597f56d" style="">​</span></p><!-- } SE-TEXT -->
</div>
</div>
</div>
</div> <div class="se-component se-quotation se-l-quotation_line" id="SE-957a2d6b-94ef-469d-ad88-d8fd3db0a83e">
<div class="se-component-content">
<div class="se-section se-section-quotation se-l-quotation_line">
<blockquote class="se-quotation-container">
<div class="se-module se-module-text se-quote"><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-8c20f235-7b9f-4879-b826-0f773fc85a8e" style=""><span class="se-fs- se-ff-" id="SE-5f8c9324-01a1-4686-9bfe-10e4fcfd1eab" style="">실행 및 파일 확인</span></p><!-- } SE-TEXT --></div>
<div class="se-module se-module-text se-cite"><p class="se-text-paragraph se-text-paragraph-align-" id="SE-34cb7b6e-3725-491e-8dbc-f9402a80720d" style=""><span class="se-fs- se-ff-" id="SE-3b94510d-602a-4056-b54f-a57bd1b318a2" style="">마무리하며</span></p></div>
</blockquote>
</div>
</div>
</div>
<div class="se-component se-text se-l-default" id="SE-78f656c1-36c2-4b6d-a489-5cfffdfb116e">
<div class="se-component-content">
<div class="se-section se-section-text se-l-default">
<div class="se-module se-module-text">
<!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-95ef5c35-29e4-49bc-b76c-0baa5f578c7f" style=""><span class="se-fs- se-ff-" id="SE-ffc82fa6-86f4-42fd-9a57-714ee62c50e5" style="">구글 클라우드 컴퓨터는 SSH 세션 연결이 끝나면 실행 중인 프로세스들도 종료하므로 백그라운드에서 실행해야 한다. 그렇기에 nohup명령어(유닉스 백그라운드 실행)로 실행했다.</span></p><!-- } SE-TEXT --><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-52a78b61-562d-4432-a247-4ce8e4fe1be7" style=""><span class="se-fs- se-ff-" id="SE-c3c29bc6-af9e-43f9-b702-ef1f37db17f6" style="">​</span></p><!-- } SE-TEXT --><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-439f9c61-9d12-44a0-ba81-363b9f795327" style=""><span class="se-fs- se-ff-" id="SE-edccc56f-91bf-436a-bc86-5628308042c6" style="">nohup python3 my_script.py &gt; ~/logs/my_script.log &amp;</span></p><!-- } SE-TEXT --><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-a6b56f6f-85a0-4a33-a947-d2df5c181f1d" style=""><span class="se-fs- se-ff-" id="SE-b3a79767-5900-4f71-8c11-d73144c93f4b" style="">&gt;은 재지정자로, 백그라운드에서 실행하면 로그가 저장되는데, 같이 저장되면 커밋에서 꼬이기 때문에 다른 디렉토리로 재지정한다.</span></p><!-- } SE-TEXT --><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-44b3b821-f7ad-4a8e-9ce1-8133a2cc4359" style=""><span class="se-fs- se-ff-" id="SE-9da6ca99-bdf9-40be-aaa1-528edfddff9b" style="">​</span></p><!-- } SE-TEXT --><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-1021e9b7-5bfb-402b-9001-ece8f8c7de23" style=""><span class="se-fs- se-ff-" id="SE-736c8c7e-d859-4b42-b69d-27b8f5e60223" style="">​</span></p><!-- } SE-TEXT --><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-d5aea2c6-3fe8-40d9-9bf4-bfc68b5ed71f" style=""><span class="se-fs- se-ff-" id="SE-37864844-3ef3-4138-9bf6-b74921f31ab9" style=""><a class="se-link" href="https://rage147-owo.github.io/VRChatKoreaNews/%EB%8F%99%EC%95%84%EC%9D%BC%EB%B3%B4.html" target="_blank">동아일보</a></span></p><!-- } SE-TEXT --><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-d8018d0d-0728-4951-9f79-5978027cd745" style=""><span class="se-fs- se-ff-" id="SE-0fbe844d-0960-48a7-b2f9-c069ccc5e9d2" style=""><a class="se-link" href="https://rage147-owo.github.io/VRChatKoreaNews/%EB%A7%A4%EC%9D%BC%EA%B2%BD%EC%A0%9C.html" target="_blank">매일경제</a></span></p><!-- } SE-TEXT --><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-51ea6188-8b42-44a2-8ed0-dbf0d5e63de7" style=""><span class="se-fs- se-ff-" id="SE-d1341262-750e-47fa-a1ee-dc21f591eff4" style=""><a class="se-link" href="https://rage147-owo.github.io/VRChatKoreaNews/%EC%A1%B0%EC%84%A0%EC%9D%BC%EB%B3%B4.html" target="_blank">조선일보</a></span></p><!-- } SE-TEXT --><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-09f0f88a-aa15-4588-9f63-f1445d6227c5" style=""><span class="se-fs- se-ff-" id="SE-4bfd9924-2772-4104-8b88-8d1a3ee82fff" style="">HTML로 github.io에서 잘 작동하는것을 볼 수 있다.</span></p><!-- } SE-TEXT --><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-0cfa6467-d819-44b4-b980-70c01add11ec" style=""><span class="se-fs- se-ff-" id="SE-388802ff-8b03-417f-ae73-57af16ad6c98" style="">​</span></p><!-- } SE-TEXT --><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-44a0317e-e3a1-49a2-b40c-4167170324a0" style=""><span class="se-fs- se-ff-" id="SE-70194cac-db54-46cd-ae22-590bebe1848b" style="">​</span></p><!-- } SE-TEXT --><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-9b2b23f6-8a04-4b9a-8122-bdbaab87f679" style=""><span class="se-fs- se-ff-" id="SE-f63008aa-3700-4f3d-82a6-b94eb05ce7b2" style="">​</span></p><!-- } SE-TEXT --><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-17712604-8849-4be7-a062-2f468b4b2baf" style=""><span class="se-fs- se-ff-" id="SE-0fef898c-f6aa-41f0-8134-29d828d57724" style=""><a class="se-link" href="https://github.com/rage147-OwO/VRChatKoreaNews" target="_blank">https://github.com/rage147-OwO/VRChatKoreaNews</a></span></p><!-- } SE-TEXT --><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-1e54135c-ab3e-4046-8e6e-3dd9e1e49986" style=""><span class="se-fs- se-ff-" id="SE-e6c7c823-71fd-401c-a3c4-96f40079367b" style="">쓸데없는 커밋이 많으니 깃허브에게 미안하기도 하다.</span></p><!-- } SE-TEXT --><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-0d823bfb-711f-4959-9ca3-5a9d70d5560e" style=""><span class="se-fs- se-ff-" id="SE-2176912d-a14f-4e99-95b0-395cea05d7ed" style="">커밋 아카이브를 끌 수 있던데, 그걸 끄면 커밋 기록을 사용하지 않을 수 있을지는 모르겠다.</span></p><!-- } SE-TEXT --><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-ac579e77-2d16-4b59-9d59-9dccf2f8dda0" style=""><span class="se-fs- se-ff-" id="SE-39709bbc-e7ae-441c-9f24-2eb4cb61f9e2" style="">​</span></p><!-- } SE-TEXT --><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-f99c0274-6ca4-497c-aa15-50fb4f6c85d8" style=""><span class="se-fs- se-ff-" id="SE-4bde3b02-26eb-4d06-bdef-0765bcc921b0" style="">시간이 나면 네이버 블로그를 RSS로 받아서 깃허브에 자동으로 연동시켜 둘 것이기 때문에 요 코드는 나중에도 요긴한게 쓰일 것 같다.</span></p><!-- } SE-TEXT --><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-41c2a48a-3cd2-4b85-aad6-41cfe5445592" style=""><span class="se-fs- se-ff-" id="SE-3f6be550-cda3-4d05-95d1-d2e445be4084" style="">​</span></p><!-- } SE-TEXT --><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-07dd6b39-76e8-4d6a-bfa5-de0209694d1a" style=""><span class="se-fs- se-ff-" id="SE-41dd771c-5c70-4f1e-83a8-b82443fe9f2b" style="">​</span></p><!-- } SE-TEXT --><!-- SE-TEXT { --><p class="se-text-paragraph se-text-paragraph-align-" id="SE-dd6b463a-edb5-4fec-97e0-bbdba840a69b" style=""><span class="se-fs- se-ff-" id="SE-29152573-421a-488f-9636-4254c5722f97" style="">다음편은 유니티 클라이언트에서의 개발이다.</span></p><!-- } SE-TEXT -->
</div>
</div>
</div>
</div> </div>
</div>
</div>