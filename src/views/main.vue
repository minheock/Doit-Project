<template>
    <section class="maincontents">
        <section class="mainbanner"><img src="/images/mainimg.png" /></section>
        <section class="newbook">
            <h1 class="maintit">
                새로 나온 도서<span>분야별로 새로 나온 도서를 만나 보세요</span>
            </h1>
            <div class="tapcontent">
                <div class="tap">
                    <b-button variant="tap active" @click="AddContents('Newbooks_it')">IT 전문서</b-button>
                    <b-button variant="tap" @click="AddContents('Newbooks_work')">업무 능력, 기타</b-button>
                    <b-button variant="tap" @click="AddContents('Newbooks_photo')">사진 예술</b-button>
                    <b-button variant="tap" @click="AddContents('Newbooks_science')">데이터 과학</b-button>
                </div>
                <VueSlickCarousel class="mainslider" v-bind="settings">
                    <div class="rollimg" v-for="(item, index) in Newbooks" :key="index">
                        <span class="imgbox"><img :src="item.imgurl"></span>
                        <strong v-html="item.name"></strong>
                        <span class="textbox" v-html="item.subdec"></span>
                    </div>
                </VueSlickCarousel>
            </div>
        </section>
        <section class="searchbook">
            <h1 class="maintit">
                도서 검색<span>찾고자 하는 도서명을 검색해 주세요</span>
            </h1>
            <div class="inputarea">
                <b-form-input />
                <b-button variant="search"><i class="bi bi-search"></i></b-button>
            </div>
            <div class="guidehash">
                <span v-for="(item, index) in hashdata" :key="index" v-html="item.text"></span>1
            </div>
        </section>
        <section class="bannermenu"></section>
        <section class="notice">
            <h1 class="maintit">
                공지 사항
            </h1>
        </section>
    </section>
</template>


<script>
export default {
    data() {
        return {
            Newbooks: [],
            Newbooks_it: [
                { imgurl: "/images/books_image/book01.jpg", name: "Do it! 웹 사이트 따라 만들기", subdec: "HTML, CSS, 자바스크립트 문법서는 공부했지만, 웹 사이트를...", },
                { imgurl: '/images/books_image/book02.jpg', name: 'Do it! 첫 알고리즘', subdec: '160가지 그림과 스토리텔링으로 이해한다! 자료구조부터 보안...' },
                { imgurl: '/images/books_image/book03.jpg', name: 'Do it! C# 프로그래밍 입문', subdec: '이 책은 기본이 충실하면서도 프로젝트 실습까지 챙긴 C# 입문서...' },
                { imgurl: '/images/books_image/book04.jpg', name: 'IT 5분 잡학사전', subdec: 'IT 분야 직장에서 일하는 나 요즘 주변에 이상한 사람이...' },
                { imgurl: '/images/books_image/book05.jpg', name: 'Do it! SQL 입문', subdec: '20년간 글로벌 기업에서 데이터베이스 전문가로 근무한 저자의...' },
                { imgurl: '/images/books_image/book06.jpg', name: 'Do it! 클론 코딩 줌', subdec: '클론 코딩 시리즈 3탄, 노마드 코더의 동영상 무료 공개! ...' },
                { imgurl: '/images/books_image/book07.jpg', name: 'Do it! 오토캐드 2023', subdec: '5년 연속 베스트셀러! 평면도 그리기부터 치수 문제 해결까지!...' }
            ],
            Newbooks_work: [
                { imgurl: "/images/books_image/book08.jpg", name: "된다! 엑셀 수식 & 함수", subdec: "매일 쓰는 엑셀이 매번 어렵게 느껴지는 건 너무 많은 기능을...", },
                { imgurl: '/images/books_image/book09.jpg', name: '일 잘하는 디자이너', subdec: '일 잘하는 디자이너가 되는 69가지 방법으로 자신을 지키면서 일...' },
                { imgurl: '/images/books_image/book10.jpg', name: '된다! 아이패드 하루 24시간', subdec: '아이패드로 하루 24시간, 365일을 알차게 보내는 방법..' },
                { imgurl: '/images/books_image/book11.jpg', name: '된다! 포토샵 디자인 수업', subdec: '온라인 강의 최고 매출 바로 그분! 아윤 쌤의 강의...' },
                { imgurl: '/images/books_image/book12.jpg', name: '된다! 하루 5분 노션 활용법', subdec: '2015년 첫 출간 이후 매년 개정되며 ‘맥북 분야 1위’를...' },
                { imgurl: '/images/books_image/book13.jpg', name: '된다! 저작권 문제 해결 ', subdec: '25년간 저작권을 다뤄온 판사 출신 변호사의 구체적인...' },
                { imgurl: '/images/books_image/book14.jpg', name: '된다! 7일 실무 엑셀 ', subdec: '이 책의 전반부에서는 타입스크립트의 핵심 문법...' }
            ],
            Newbooks_photo: [
                { imgurl: "/images/books_image/book15.jpg", name: "포토샵 보정&합성 디자인 사전", subdec: "포토샵 사진 보정, 합성 때문에 고민인가요? 한 권으로 상위...", },
                { imgurl: '/images/books_image/book16.jpg', name: '된다! 깨비의 DSLR...', subdec: '카메라 초보도 3일이면 인물, 풍경 출사 갈 수 있다!...' },
                { imgurl: '/images/books_image/book17.jpg', name: '프로 사진가들의 아름다운...', subdec: '아름다운 사진을 촬영하기 위한 구도와 카메라 설정 그리고 색과 ...' },
                { imgurl: '/images/books_image/book18.jpg', name: '프로 사진가들이 알려주는...', subdec: '일본 프로 사진가들의 노하우를 모은 DCM 시리즈에 연재된 ...' },
                { imgurl: '/images/books_image/book19.jpg', name: '프로 사진가들의 사진 보정...', subdec: '일본 최고 사진가의 노하우가 담긴 잡지, DCM 시리즈의...' },
                { imgurl: '/images/books_image/book20.jpg', name: '프로 사진가들이 사용하는...', subdec: '이 책은 일본의 프로 사진가들이 사진을 촬영할 때 노출을...' }
            ],
            Newbooks_science: [
                { imgurl: "/images/books_image/book21.jpg", name: "블록체인 무엇인가?", subdec: "이 책은 과장된 소문에 휘둘리지도, 비트코인에 집중하지도 않는...", },
                { imgurl: '/images/books_image/book22.jpg', name: '빅데이터, 승리의 과학', subdec: '2012년, 혼전을 거듭한 미국 대통령 선거에서 민주당...' },
                { imgurl: '/images/books_image/book23.jpg', name: '데이터는 어떻게 자산이...', subdec: '데이터는 4차 산업혁명의 원동력으로서...' },
                { imgurl: '/images/books_image/book24.jpg', name: '기계는 어떻게 생각하는가?', subdec: '구글 엔지니어링 팀 수석 리더인 숀 게리시는 컴퓨터...' },
                { imgurl: '/images/books_image/book25.jpg', name: '데이터 과학, 무엇을 하는가?', subdec: '미국 제너럴 모터스부터 한국의 대기업 통신회사 및...' },
                { imgurl: '/images/books_image/book26.jpg', name: '빅데이터의 다음 단계는...', subdec: '이 책, <예측 분석이다>에서는 도대체 어떻게 이러한...' }

            ],
            settings: {
                slidesToShow: 5, // 화면의 나타날 슬라이드 개수
                arrows: true,
                dots: false,
                infinite: true,
                responsive: [
                    {
                        breakpoint: 767,
                        settings: {
                            slidesToShow: 4,
                        },
                    },
                    {
                        breakpoint: 414,
                        settings: {
                            slidesToShow: 2,
                        },
                    },
                ]
            }
            ,
            hashdata: [
                { text: "html", value: "html" },
                { text: "vue", value: "vue" },
                { text: "css", value: "css" },
                { text: "javascript", value: "javascript" },
                { text: "자료구조/알고리즘", value: "자료구조/알고리즘" },
                { text: "파이썬", value: "파이썬" },
            ],
        }
    },
    created() {
        this.Newbooks = this.Newbooks_it;
    },
    methods: {
        AddContents(contents) {
            this.Newbooks = this[contents]

            console.log(1111 + contents);
            console.log(2222 + this[contents]);
            document.querySelector(".active").classList.remove("active");
            event.target.classList.add("active");
        }
    },
}
</script>
