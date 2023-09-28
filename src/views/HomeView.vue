<template>
  <div class="menu-page">
    <div class="page-left">
      <div class="set-menu-top">
        <button
          class="set-btn"
          v-for="(item, index) in setTitleBtnList"
          :key="index"
          :class="selectTitleBtnId === item.id ? 'set-active' : ''"
          @click="setActive(item)"
        >
          {{ item.name }}
        </button>
      </div>
      <div class="set-menu-bottom">
        <div v-show="selectTitleBtnId === 1" class="set-box">
          <div class="set-val-row">
            <div class="set-val-title">平移按钮组 X</div>
            <input type="text" class="set-val-input" v-model="btnGroupLeft" />
          </div>
          <div class="set-val-row">
            <div class="set-val-title">平移按钮组 Y</div>
            <input type="text" class="set-val-input" v-model="btnGroupTop" />
          </div>
          <!-- <div class="set-val-row">
            <div class="set-val-title">默认按钮贴图</div>
            <input type="text" class="set-val-input" />
          </div> -->
        </div>
        <div v-show="selectTitleBtnId === 2" class="set-box">
          <div class="btn-list-num">
            <div
              class="select-btn-row"
              v-for="(item, index) in btnGroupList"
              :key="index"
              :class="setBtnGroupId === index ? 'set-active' : ''"
              @click="selectActive(item, index)"
            >
              {{ index + 1 }}
            </div>
            <div>
              <div class="set-val-row">
                <div class="set-val-title">按钮名称</div>
                <input
                  type="text"
                  class="set-val-input"
                  v-model="btnGroupList[setBtnGroupId].btnName"
                />
              </div>
              <div class="set-val-row">
                <div class="set-val-title">是否显示按钮</div>
                <input
                  type="text"
                  class="set-val-input"
                  v-model="btnGroupList[setBtnGroupId].isShowBtn"
                />
              </div>
              <div class="set-val-row">
                <div class="set-val-title">是否激活按钮</div>
                <input
                  type="text"
                  class="set-val-input"
                  v-model="btnGroupList[setBtnGroupId].isActivationBtn"
                />
              </div>
              <div class="">
                <div class="set-val-title textarea-title">激活运行代码</div>
                <textarea
                  class="set-val-input textarea-input"
                  name=""
                  id=""
                  cols="25"
                  rows="5"
                  v-model="btnGroupList[setBtnGroupId].runCode"
                ></textarea>
              </div>
            </div>
          </div>
        </div>
        <div v-show="selectTitleBtnId === 3" class="set-box">
          <div class="btn-list-num">
            <div
              class="select-btn-row"
              v-for="(item, index) in btnGroupOtherList"
              :key="index"
              :class="setOtherBtnGroupId === index ? 'set-active' : ''"
              @click="selectActive(item, index)"
            >
              {{ index + 1 }}
            </div>
            <div>
              <div class="set-val-row">
                <div class="set-val-title">按钮X坐标</div>
                <input
                  type="text"
                  class="set-val-input"
                  v-model="btnGroupOtherList[setOtherBtnGroupId].btnLeft"
                />
              </div>
              <div class="set-val-row">
                <div class="set-val-title">按钮Y坐标</div>
                <input
                  type="text"
                  class="set-val-input"
                  v-model="btnGroupOtherList[setOtherBtnGroupId].btnTop"
                />
              </div>
              <div class="">
                <div class="set-val-title textarea-title">按钮贴图</div>
                <!-- <input
                  type="text"
                  class="set-val-input"
                  v-model="btnGroupOtherList[setOtherBtnGroupId].background"
                /> -->
                <textarea
                  class="set-val-input textarea-input"
                  name=""
                  id=""
                  cols="25"
                  rows="3"
                  v-model="btnGroupOtherList[setOtherBtnGroupId].backgroundStr"
                  @change="changeImg(setOtherBtnGroupId)"
                ></textarea>
              </div>
              <div class="set-val-row">
                <div class="set-val-title">按钮样式</div>
                <input
                  type="text"
                  class="set-val-input"
                  v-model="btnGroupOtherList[setOtherBtnGroupId].btnStyle"
                />
              </div>
              <div class="set-val-row">
                <div class="set-val-title">是否显示按钮</div>
                <input
                  type="text"
                  class="set-val-input"
                  v-model="btnGroupOtherList[setOtherBtnGroupId].isShowBtn"
                />
              </div>
              <div class="set-val-row">
                <div class="set-val-title">是否激活按钮</div>
                <input
                  type="text"
                  class="set-val-input"
                  v-model="
                    btnGroupOtherList[setOtherBtnGroupId].isActivationBtn
                  "
                />
              </div>
              <div class="set-val-row">
                <div class="set-val-title">按钮激活效果</div>
                <input
                  type="text"
                  class="set-val-input"
                  v-model="
                    btnGroupOtherList[setOtherBtnGroupId].activationMethod
                  "
                />
              </div>
              <div class="">
                <div class="set-val-title textarea-title">激活运行代码</div>
                <textarea
                  class="set-val-input textarea-input"
                  name=""
                  id=""
                  cols="25"
                  rows="5"
                  v-model="btnGroupOtherList[setOtherBtnGroupId].runCode"
                ></textarea>
              </div>
              <div class="">
                <div class="set-val-title textarea-title">激活访问网址</div>
                <textarea
                  class="set-val-input textarea-input"
                  name=""
                  id=""
                  cols="25"
                  rows="5"
                  v-model="btnGroupOtherList[setOtherBtnGroupId].runPage"
                ></textarea>
              </div>
              <div class="set-val-row">
                <div class="set-val-title">访问方式</div>
                <input
                  type="text"
                  class="set-val-input"
                  v-model="btnGroupOtherList[setOtherBtnGroupId].openMethod"
                />
              </div>
            </div>
          </div>
        </div>
        <div v-if="selectTitleBtnId === 4">4</div>
      </div>
    </div>
    <div class="page-right">
      <div
        class="game-page"
        :style="{ width: pageWidth + 'px', height: pageHeight + 'px' }"
      >
        <div class="back_title"></div>
        <div class="back_title2"></div>
        <!-- 开始游戏 按钮组 -->
        <div
          class="menu-btn-group"
          :style="{
            position: btnMode === 'btnGroup' ? 'absolute' : 'relative',
            top: btnGroupTop + 'px',
            left: btnGroupLeft + 'px',
          }"
        >
          <button
            class="menu-btn"
            v-for="(item, index) in btnGroupList"
            :style="{
              top: item.btnTop + 'px',
              left: item.btnLeft + 'px',
              position: item.btnMode,
            }"
            :key="index"
          >
            {{ item.btnName }}
          </button>
        </div>
        <!-- 其他按钮组 -->
        <div class="other-btn-group">
          <div
            class="other-btn"
            v-for="(item, index) in btnGroupOtherList"
            :style="{
              top: item.btnTop + 'px',
              left: item.btnLeft + 'px',
            }"
            :key="index"
            @click="clickEvent(item)"
          >
            <img :src="`${item.background}`" alt="" />
          </div>
        </div>
        <div
          class="title-extra-info"
          :style="{
            width: titleExtraInfo.width + 'px',
            height: titleExtraInfo.height + 'px',
            lineHeight: titleExtraInfo.lineHeight * 2 + 'px',
            top: titleExtraInfo.top + 'px',
            left: titleExtraInfo.left + 'px',
            justifyContent: titleExtraInfo.flex,
          }"
        >
          {{ titleExtraInfo.text }}
        </div>
      </div>
    </div>
  </div>
</template>

<script>
const shell = window.require("electron").shell;
export default {
  name: "HomeView",
  props: {
    msg: String,
  },
  data() {
    return {
      pageWidth: 1366,
      pageHeight: 768,
      btnTop1: 0,
      btnLeft1: 0,
      btnTop2: 0,
      btnLeft2: 0,
      btnTop3: 0,
      btnLeft3: 0,
      btnTop4: 0,
      btnLeft4: 0,
      // onlyOne 单独设置按钮  btnGroup 按钮组
      btnMode: "btnGroup",
      btnGroupTop: 550,
      btnGroupLeft: 683,
      btnGroupList: [
        {
          btnName: "重新开始",
          isShowBtn: true,
          isActivationBtn: true,
          runCode: "this.commandNewGame();",
          btnTop: 0,
          btnLeft: 0,
          btnMode: "btnGroup", //absolute
        },
        {
          btnName: "继续游戏",
          isShowBtn: true,
          isActivationBtn: true,
          runCode: "SceneManager.push(Scene_Load);",
          btnTop: 0,
          btnLeft: 0,
          btnMode: "btnGroup", //absolute
        },
        {
          btnName: "选项",
          isShowBtn: true,
          isActivationBtn: true,
          runCode: "SceneManager.push(Scene_Options);",
          btnTop: 0,
          btnLeft: 0,
          btnMode: "btnGroup", //absolute
        },
        {
          btnName: "游戏结束",
          isShowBtn: true,
          isActivationBtn: true,
          runCode: "SceneManager.exit();",
          btnTop: 0,
          btnLeft: 0,
          btnMode: "btnGroup", //absolute
        },
      ],
      setBtnGroupId: 0,
      btnGroupOtherList: [
        {
          btnName: "新按钮",
          btnTop: 730,
          btnLeft: 1300,
          backgroundStr: "btn_project1.png",
          background: require("../assets/imgs/titles1/btn_project1.png"),
          btnStyle: 4,
          isShowBtn: "true", // 是否显示按钮
          isActivationBtn: "true", // 是否激活按钮
          activationMethod: "访问网站", // 激活效果
          openMethod: "新建窗口", // 访问方式
          runCode: "", // 按钮激活运行代码
          runPage: "https://rpg.blue/thread-493213-1-1.html", // 按钮激活访问网站
        },
        {
          btnName: "新按钮",
          btnTop: 730,
          btnLeft: 1200,
          background: require("../assets/imgs/titles1/btn_afadian.png"),
          btnStyle: 4,
          isShowBtn: "true", // 是否显示按钮
          isActivationBtn: "true", // 是否激活按钮
          activationMethod: "访问网站", // 激活效果
          openMethod: "新建窗口", // 访问方式
          runCode: "", // 按钮激活运行代码
          runPage: "https://afdian.net/a/ganfly", // 按钮激活访问网站
        },
        {
          btnName: "新按钮",
          btnTop: 730,
          btnLeft: 1130,
          background: require("../assets/imgs/titles1/btn_bilibili.png"),
          btnStyle: 4,
          isShowBtn: "true", // 是否显示按钮
          isActivationBtn: "true", // 是否激活按钮
          activationMethod: "访问网站", // 激活效果
          openMethod: "新建窗口", // 访问方式
          runCode: "", // 按钮激活运行代码
          runPage: "https://space.bilibili.com/29393711", // 按钮激活访问网站
        },
        {
          btnName: "新按钮",
          btnTop: 730,
          btnLeft: 50,
          background: require("../assets/imgs/titles1/btn_credit.png"),
          btnStyle: 4,
          isShowBtn: "true", // 是否显示按钮
          isActivationBtn: "true", // 是否激活按钮
          activationMethod: "运行代码", // 激活效果
          openMethod: "新建窗口", // 访问方式
          runCode: "SceneManager.push(Scene_Credit);", // 按钮激活运行代码
          runPage: "", // 按钮激活访问网站
        },
      ],
      setOtherBtnGroupId: 0,
      titleExtraInfo: {
        text: "GF插件库v1.03版本",
        top: 730,
        left: 0,
        width: 1366,
        height: 50,
        lineHeight: 24,
        flex: "center",
      },
      setTitleBtnList: [
        {
          id: 1,
          name: "标题命令按钮总体设置",
          isSelect: true,
        },
        {
          id: 2,
          name: "标题命令按钮分项设置",
          isSelect: false,
        },
        {
          id: 3,
          name: "标题额外按钮设置",
          isSelect: false,
        },
        {
          id: 4,
          name: "标题额外信息窗口设置",
          isSelect: false,
        },
      ],
      selectTitleBtnId: 3,
    };
  },
  mounted() {
    console.log();
    // this.btnGroupOtherList[0].background = require("../assets/imgs/titles1/back_title.png");
  },
  methods: {
    // 其他按钮点击事件
    clickEvent(item) {
      console.log(item);
      if (!item.runPage) return;
      shell.openExternal(item.runPage);
    },
    setActive(item) {
      this.setTitleBtnList.forEach((col) => {
        col.isSelect = false;
      });
      this.selectTitleBtnId = item.id;
      if (!item.isSelect) item.isSelect = true;
    },
    selectActive(item, index) {
      console.log(item, index);
      this.setBtnGroupId = index;
    },
    changeImg(idx) {
      console.log(idx);
      let that = this;
      try {
        this.btnGroupOtherList[
          idx
        ].background = require(`@/assets/imgs/titles1/${this.btnGroupOtherList[idx].backgroundStr}`);
        // `../assets/imgs/titles1/back_title.png`);
        // let imgSrc = that.btnGroupOtherList[idx].backgroundStr;
        // console.log(imgSrc);
        // that.btnGroupOtherList[
        //   idx
        // ].background = require(`../assets/imgs/${imgSrc}`);
      } catch (error) {
        console.log(error);
        that.btnGroupOtherList[idx].background = "";
      }
    },
  },
};
</script>
<style scoped lang='less'>
.menu-page {
  height: 100%;
  display: flex;
  .page-left {
    padding-top: 10px;
    width: 250px;
    border: 1px solid #ccc;
    .set-menu-top {
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      border-bottom: 1px solid #ccc;
      .set-btn {
        width: 150px;
        margin-bottom: 10px;
      }
    }
    .set-menu-bottom {
      overflow-y: auto;
      height: calc(100% - 200px);
      padding: 10px 20px;
      .set-box {
        .btn-list-num {
          display: flex;
          flex-wrap: wrap;
          .select-btn-row {
            border: 1px solid #ccc;
            border-radius: 3px;
            width: 30px;
            height: 30px;
            line-height: 30px;
            text-align: center;
            margin: 0 10px 10px 0;
            cursor: pointer;
          }
        }
        .set-val-row {
          display: flex;
          align-items: center;
          margin-bottom: 10px;
          .set-val-title {
            width: 90px;
            margin-right: 10px;
          }
          .set-val-input {
            width: 80px;
          }
        }
        .textarea-title,
        .textarea-input {
          margin-bottom: 10px;
        }
      }
    }
  }
  .page-right {
    .game-page {
      overflow: hidden;
      position: relative;
      border: 1px solid #ccc;
    }
    .back_title,
    .back_title2 {
      position: absolute;
      width: 100%;
      height: 100%;
    }
    .back_title {
      background: url("../assets/imgs/titles1/back_title.png") no-repeat;
    }
    .back_title2 {
      background: url("../assets/imgs/titles2/back_title_2.png") no-repeat;
    }
    .menu-btn-group {
      display: flex;
      flex-direction: column;
      transform: translateY(-16px) translateX(-48%);
      :hover {
        transform: scale(1.04);
        transition: all 0.4s;
      }
      .menu-btn {
        z-index: 5;
        transition: all 0.4s;
        cursor: pointer;
        margin-bottom: 10px;
        color: #fff;
        font-size: 24px;
        width: 180px;
        height: 40px;
        line-height: 40px;
        background: url("../assets/imgs/titles1/btn_title.png") no-repeat;
        background-size: 100% 100%;
      }
    }
    .other-btn-group {
      .other-btn {
        z-index: 5;
        cursor: pointer;
        position: absolute;
        background-size: 100% 100% !important;
        transform: translateY(-16px) translateX(-48%);
        img {
          opacity: 0.6;
          transition: all 0.4s;
        }
        &:hover img {
          transition: all 0.4s;
          opacity: 0.9;
        }
      }
    }
    .title-extra-info {
      color: #fff;
      position: absolute;
      display: flex;
      z-index: 3;
    }
  }
}
</style>
