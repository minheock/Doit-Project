<template>
    <header>
        <div class="topmenu">
            <div class="contentbox">
                <div class="logo">
                    <button @click="goTopage('/main')">
                        <img src="/images/logo.png" alt="이지스퍼블리싱 로고">
                    </button>
                </div>
                <div class="system">
                    <button class="login" v-b-modal.login>로그인</button>
                    <button class="member" v-b-modal.member>회원가입</button>
                </div>
            </div>
        </div>
        <nav>
            <div class="contentbox">
                <ul>
                    <li v-for="(item, idx) in menulists" :key="idx" @click="goTopage(item.link)">
                        <button v-html="item.menutext"></button>
                    </li>
                </ul>
            </div>
        </nav>
        <b-modal id="login" class="modal" hide-footer>
            <template #modal-title>
                <div class="layertit"><i class="bi bi-clipboard-check" /> 로그인</div>
            </template>
            <div class="modalcontainer">
                <div class="loginform">
                    <!-- 아이디 입력란 -->
                    <label for="id"><i class="bi bi-file-person" /> 아이디</label>
                    <b-form-input id="id" placeholder="아이디를 입력해 주세요" />
                    <!-- 비번 입력란 -->
                    <label for="pw"><i class="bi bi-lock" /> 비밀번호</label>
                    <b-form-input type="password" id="pw" placeholder="비밀번호를 입력해 주세요" />
                </div>
                <div class="btnwrap">
                    <b-button variant="login">로그인</b-button>
                </div>
            </div>
        </b-modal>
        <b-modal id="member" class="modal" hide-footer>
            <template #modal-title>
                <div class="layertit"><i class="bi bi-clipboard-check" /> 회원가입</div>
            </template>
            <div class="modalcontainer">
                <b-form>
                    <!-- 아이디 입력란 -->
                    <b-form-group id="formid1" label="아이디" label-for="id" description="4 ~ 15자리 이내의 영문과 숫자로만 입력하세요.">
                        <b-form-input id="id" v-model="form.id" type="text" placeholder="아이디를 입력해 주세요" required>
                        </b-form-input>
                        <b-button>중복 확인</b-button>
                    </b-form-group>
                    <!-- 비밀번호 입력란 -->
                    <b-form-group id="formid2" label="비밀번호" label-for="password" description="8자리 이상의 영문과 숫자로만 입력하세요.">
                        <b-form-input id="password" v-model="form.pw" type="password" placeholder="비밀번호를 입력해 주세요"
                            required>
                        </b-form-input>
                    </b-form-group>
                    <!-- 이메일 입력란 -->
                    <b-form-group id="formid3" label="이메일 수신" label-for="mailing"
                        description="이메일 수신을 허락하면 독자 혜택을 받을 수 있어요.">
                        <b-form-radio value="Y" v-model="form.mail">예</b-form-radio>
                        <b-form-radio value="N" v-model="form.mail">아니오</b-form-radio>

                    </b-form-group>
                    <!-- 체크박스 입력란 -->
                    <b-form-group id="formid4" label="관심분야 선택" label-for="checkedtype"
                        description="※ 관심 분야를 선택하세요. 여러 개 선택할 수 있어요.">
                        <b-form-checkbox value="html" v-model="form.checkedtype">HTML/CSS</b-form-checkbox>
                        <b-form-checkbox value="JacaScript" v-model="form.checkedtype">JacaScript</b-form-checkbox>
                        <b-form-checkbox value="Python" v-model="form.checkedtype">Python</b-form-checkbox>
                        <b-form-checkbox value="Vue.js" v-model="form.checkedtype">Vue.js</b-form-checkbox>
                        <b-form-checkbox value="Angular" v-model="form.checkedtype">Angular</b-form-checkbox>
                        <b-form-checkbox value="React" v-model="form.checkedtype">React</b-form-checkbox>
                        <b-form-checkbox value="Data" v-model="form.checkedtype">자료구조/알고리즘</b-form-checkbox>
                        <b-form-checkbox value="CAD" v-model="form.checkedtype">Auto CAD</b-form-checkbox>
                    </b-form-group>
                    <div class="btnwrap half">
                        <b-button type="submit" variant="login">확인</b-button>
                        <b-button type="reset" variant="cancel">취소</b-button>
                    </div>
                </b-form>
            </div>
        </b-modal>
    </header>
</template>

<script>
export default {
    data() {
        return {
            menulists: [
                { menutext: "도서소개", link: "/book" },
                { menutext: "자료실", link: "/reference" },
                { menutext: "동영상 강의", link: "/movieclass" },
                { menutext: "교재 샘플", link: "/classsample" },
                { menutext: "회사 소개", link: "/company" }
            ],
            form: {
                id: "",
                pw: "",
                mail: "",
                checkedtype: []
            }
        }
    },
    methods: {
        goTopage(target) {
            if (this.$router.currentRoute.path !== target) {
                this.$router.push(target);
            }
        }
    },
    JoinMember(e) {
        e.preventDefault();
        alert(JSON.stringify(this.form));
        this.$nextTick(() => {
            this.form.id = "";
            this.form.pw = "";
            this.form.mail = "";
            this.form.checkedtype = [];
        })
    }
}

</script>