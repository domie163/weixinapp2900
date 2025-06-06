
<template>
    <view class="content">
        <form class="app-update-pv">
                 <view
                         :style='{"boxShadow":"0","backgroundColor":"rgba(255, 255, 255, 0.25)","borderColor":"rgba(228, 232, 230, 1)","margin":"0 0 0px 0","borderWidth":"2rpx","borderStyle":"none none solid none ","height":"88rpx"}'
                         class="cu-form-group">
                     <view :style='{"width":"160rpx","fontSize":"28rpx","color":"#FE8010","textAlign":"left"}'
                           class="title">课程名称</view>
                     <input   disabled
                              :style='{"boxShadow":"0 0 16rpx #F37335 inset","backgroundColor":"rgba(255, 255, 255, 1)","borderColor":"#FE8010","borderRadius":"20rpx","color":"#FE8010","textAlign":"left","borderWidth":"2rpx","fontSize":"28rpx","borderStyle":"solid","height":"88rpx","marginTop":"7rpx"}'
                              :disabled="ro.kechengName" v-model="kecheng.kechengName" placeholder="课程名称"></input>
                 </view>
                <view
                        :style='{"boxShadow":"0","backgroundColor":"rgba(255, 255, 255, 0.25)","borderColor":"rgba(228, 232, 230, 1)","margin":"0 0 0px 0","borderWidth":"2rpx","borderStyle":"none none solid none ","height":"88rpx"}'
                        class="cu-form-group">
                    <view :style='{"width":"160rpx","fontSize":"28rpx","color":"#FE8010","textAlign":"left"}'
                          class="title">课程类型</view>
                    <input disabled
                           :style='{"boxShadow":"0 0 16rpx #F37335 inset","backgroundColor":"rgba(255, 255, 255, 1)","borderColor":"#FE8010","borderRadius":"20rpx","color":"#FE8010","textAlign":"left","borderWidth":"2rpx","fontSize":"28rpx","borderStyle":"solid","height":"88rpx","marginTop":"7rpx"}'
                           :disabled="ro.kechengValue"
                           v-model="kecheng.kechengValue"
                           placeholder="课程类型"></input>
                </view>
                <view
                        :style='{"boxShadow":"0 0 0px rgba(0,0,0,.3)","backgroundColor":"rgba(255, 255, 255, 0.25)","borderColor":"rgba(218, 220, 219, 1)","margin":"0 0 0px 0","borderWidth":"2rpx","borderStyle":"none none solid none ","height":"108rpx"}'
                        class="cu-form-group">
                    <view :style='{"width":"160rpx","fontSize":"28rpx","color":"#FE8010","textAlign":"left"}'
                          class="title">课程封面</view>
                    <view class="right-input" style="padding:0;textAlign:left">
                        <image
                                :style='{"width":"68rpx","boxShadow":"0 0 0px rgba(0,0,0,.3)","borderRadius":"100%","textAlign":"left","height":"68rpx"}'
                                class="avator" v-if="kecheng.kechengPhoto" :src="kecheng.kechengPhoto" mode="aspectFill">
                        </image>
                        <image
                                :style='{"width":"68rpx","boxShadow":"0 0 0px rgba(0,0,0,.3)","borderRadius":"100%","textAlign":"left","height":"68rpx"}'
                                class="avator" v-else src="../../static/gen/upload.png" mode="aspectFill"></image>
                    </view>
                </view>
							                 <view
                         :style='{"boxShadow":"0","backgroundColor":"rgba(255, 255, 255, 0.25)","borderColor":"rgba(228, 232, 230, 1)","margin":"0 0 0px 0","borderWidth":"2rpx","borderStyle":"none none solid none ","height":"88rpx"}'
                         class="cu-form-group">
                     <view :style='{"width":"160rpx","fontSize":"28rpx","color":"#FE8010","textAlign":"left"}'
                           class="title">课程时常</view>
                     <input   disabled
                              :style='{"boxShadow":"0 0 16rpx #F37335 inset","backgroundColor":"rgba(255, 255, 255, 1)","borderColor":"#FE8010","borderRadius":"20rpx","color":"#FE8010","textAlign":"left","borderWidth":"2rpx","fontSize":"28rpx","borderStyle":"solid","height":"88rpx","marginTop":"7rpx"}'
                              :disabled="ro.kechengShichang" v-model="kecheng.kechengShichang" placeholder="课程时常"></input>
                 </view>
            <view
                    :style='{"boxShadow":"0","backgroundColor":"rgba(255, 255, 255, 0.25)","borderColor":"rgba(228, 232, 230, 1)","margin":"0 0 0px 0","borderWidth":"2rpx","borderStyle":"none none solid none ","height":"88rpx"}'
                    class="cu-form-group">
                <view :style='{"width":"160rpx","fontSize":"28rpx","color":"#FE8010","textAlign":"left"}'
                      class="title">订单号</view>
                <input   disabled
                         :style='{"boxShadow":"0 0 16rpx #F37335 inset","backgroundColor":"rgba(255, 255, 255, 1)","borderColor":"#FE8010","borderRadius":"20rpx","color":"#FE8010","textAlign":"left","borderWidth":"2rpx","fontSize":"28rpx","borderStyle":"solid","height":"88rpx","marginTop":"7rpx"}'
                         :disabled="ro.kechengOrderUuidNumber" type="text" v-model="ruleForm.kechengOrderUuidNumber" placeholder="订单号"></input>
            </view>
                <!-- 级联表的表id -->
                <input type="hidden" :value="kecheng.id" id="kechengId" name="kechengId"/>

            <view class="btn">
                <button
                        :style='{"boxShadow":"0 0 16rpx rgba(0,0,0,0) inset","backgroundColor":"#FE8010","borderColor":"#409EFF","borderRadius":"8rpx","color":"rgba(255, 255, 255, 1)","borderWidth":"0","width":"70%","fontSize":"32rpx","borderStyle":"solid","height":"80rpx"}'
                        @tap="onSubmitTap" class="bg-red">提交</button>
            </view>
        </form>

					<w-picker mode="dateTime" step="1" :current="false" :hasSecond="false" @confirm="insertTimeConfirm"
                              ref="insertTime" themeColor="#333333"></w-picker>
					<w-picker mode="dateTime" step="1" :current="false" :hasSecond="false" @confirm="createTimeConfirm"
                              ref="createTime" themeColor="#333333"></w-picker>


    </view>
</template>

<script>
    import wPicker from "@/components/w-picker/w-picker.vue";

    export default {
        data() {
            return {
                cross: '',
                ro:{
					kechengOrderUuidNumber: true,
					kechengId: false,
					yonghuId: false,
					kechengOrderTruePrice: false,
					insertTime: false,
					createTime: false,
        },
            ruleForm: {
					kechengOrderUuidNumber: this.getUUID(),//数字
					kechengId: '',
					yonghuId: '',
					kechengOrderTruePrice: '',
					insertTime: '',
					createTime: '',
            },
            // 登陆用户信息
            user: {},

        }
        },
        components: {
            wPicker
        },
        computed: {
            baseUrl() {
                return this.$base.url;
            },
        },
        async onLoad(options) {



            // 如果是更新操作
            if (options.id) {
                this.ruleForm.id = options.id;
                // 获取信息
                let res = await this.$api.info(`kechengOrder`, this.ruleForm.id);
                this.ruleForm = res.data;
            }
            if(options.kechengOrderId){
                this.ruleForm.kechengOrderId = options.kechengOrderId;
            }
            // 跨表
            // this.styleChange()
        },
        methods: {
            // 下拉变化


            // styleChange() {
            // 	this.$nextTick(() => {
            // 		// document.querySelectorAll('.app-update-pv .cu-form-group .uni-yaoxianStyle-yaoxianStyle').forEach(el=>{
            // 		//   el.style.backgroundColor = this.addUpdateForm.yaoxianStyle.content.backgroundColor
            // 		// })
            // 	})
            // },


			// 日期控件
			insertTimeConfirm(val) {
                console.log(val)
                this.ruleForm.insertTime = val.result;
                this.$forceUpdate();
            },
			// 日期控件
			createTimeConfirm(val) {
                console.log(val)
                this.ruleForm.createTime = val.result;
                this.$forceUpdate();
            },




            getUUID() {
                return new Date().getTime();
            },
            async onSubmitTap() {
				if ((!this.ruleForm.kechengOrderUuidNumber)) {
                    this.$utils.msg(`订单号不能为空`);
                    return
                }
                if (this.ruleForm.id) {
                    await this.$api.update(`kechengOrder`, this.ruleForm);
                } else {
                    await this.$api.save(`kechengOrder`, this.ruleForm);
                }
                uni.setStorageSync('pingluenStateState', true);
                this.$utils.msgBack('提交成功');
            },
            getDate(type) {
                const date = new Date();
                let year = date.getFullYear();
                let month = date.getMonth() + 1;
                let day = date.getDate();
                if (type === 'start') {
                    year = year - 60;
                } else if (type === 'end') {
                    year = year + 2;
                }
                month = month > 9 ? month : '0' + month;;
                day = day > 9 ? day : '0' + day;
                return `${year}-${month}-${day}`;
            },
            toggleTab(str) {
                this.$refs[str].show();
            }
        }
    }
</script>

<style lang="scss" scoped>
    .container {
        padding: 20upx;
    }

    .content:after {
        position: fixed;
        top: 0;
        right: 0;
        left: 0;
        bottom: 0;
        content: '';
        background-attachment: fixed;
        background-size: cover;
        background-position: center;
    }

    textarea {
        border: 1upx solid #EEEEEE;
        border-radius: 20upx;
        padding: 20upx;
    }

    .title {
        width: 180upx;
    }

    .avator {
        width: 150upx;
        height: 60upx;
    }

    .right-input {
        flex: 1;
        text-align: left;
        padding: 0 24upx;
    }

    .cu-form-group.active {
        justify-content: space-between;
    }

    .btn {
        display: flex;
        align-items: center;
        justify-content: center;
        flex-wrap: wrap;
        padding: 20upx 0;
    }

    .cu-form-group {
        padding: 0 24upx;
        background-color: transparent;
        min-height: inherit;
    }

    .cu-form-group+.cu-form-group {
        border: 0;
    }

    .cu-form-group uni-input {
        padding: 0 30upx;
    }

    .uni-input {
        padding: 0 30upx;
    }

    .cu-form-group uni-textarea {
        padding: 30upx;
        margin: 0;
    }

    .cu-form-group uni-picker::after {
        line-height: 68rpx;
    }

    .select .uni-input {
        line-height: 68rpx;
    }

    .input .right-input {
        line-height: 68rpx;
    }
</style>