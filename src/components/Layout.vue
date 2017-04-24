<template>
    <div class="layout">
        <div class="head">
            <h3>Readhub</h3>
        </div>
        <div class="nav">
            <div class="nav-container">
                <a v-bind:class="{active: showTab == 'HitTopics'}" v-on:click="change('HitTopics')">热门话题</a>
                <a v-bind:class="{active: showTab == 'News'}" v-on:click="change('News')">最新资讯</a>
            </div>
        </div>

        <HitTopics v-bind:hitTopics="hitTopics" v-show="showTab == 'HitTopics'" v-on:toggleInfo="toggleInfo" />
        <News v-bind:news="news" v-show="showTab == 'News'" v-on:toggleInfo="toggleInfo" />
        <LoadButton v-on:click.native="load" />

        <div id="fixedTools" class="hidden">
            <a id="backtop" href="#">↑</a>
        </div>
    </div>
    </div>
</template>
<script>
    import HitTopics from './HitTopics';
    import News from './News';
    import LoadButton from './LoadButton';

    window.onscroll = function(e) {
        if (document.body.scrollTop > 200) {
            document.querySelector('#fixedTools').classList.remove('hidden');
        } else {
            document.querySelector('#fixedTools').classList.add('hidden');
        }
    }

    export default {
        name: 'Layout',
        components: {
            HitTopics, News, LoadButton
        },
        methods: {
            change(name) {
                this.showTab = name;
            },
            toggleInfo(item) {
                item.show = !item.show;
            },
            load() {
                console.log('asdf');
                let arrMap = {
                    'HitTopics': this.hitTopics,
                    'News': this.news
                }
                let lastest = [{
                    title: '腾讯 1.43 亿美元战略入股西山居 游戏领域巨无霸诞',
                    info: '今日晚间，金山软件（HK：03888）发布公告称，腾讯斥资1.43亿美元战略入股金山软件控股子公司西山居。交易完成后，腾讯将总共持有90,896,795股西山居股份，占西山居已发行股份总数的9.9%。西山居估值达15亿美元。未来，西山居与腾讯双方将在游戏业务合作层面进行升级，西山居可以充分利用腾讯的资源优势，继续扩充核心用户、提高市场份额。同时腾讯通过西山居的优质自研产品，提升市场竞争力。',
                    show: false
                }, {
                    title: 'S8 今日全球发售 三星称将用软件升级解决屏幕泛红问',
                    info: '三星电子发言人对媒体表示，目前接到了部分用户对于 S8 屏幕呈现泛红色的报告，下周，三星将为所有的 S8 手机用户升级软件，解决这一问题。',
                    show: false
                }, {
                    title: '​北京拟出台共享单车指导意见：车辆能定位 押金必受监',
                    info: '北京市就《鼓励规范发展共享自行车的指导意见（试行）》向社会公开征求意见。要求有序停放、共享单车必须有定位系统、含保险，保证信息安全。',
                    show: false
                }, {
                    title: '各业务表现几乎全面提升 索尼将年利润预期上调 ',
                    info: '据《金融时报》北京时间 4 月 21 日报道，由于预计几乎所有业务部门的表现都有所提升，索尼公司在周五把 2017 财年营业利润预期上调近 19%，把税前利润预期上调近 28%。和 2 月份的预期相比，索尼并没有调整 2017 财年营收数据，但是将合并营业利润预期上调 18.8%至 2850 亿日元(约合 26 亿美元)，和 2016 财年相比下滑 3.1%。',
                    show: false
                }];
                let arr = arrMap[this.showTab];
                lastest.forEach(item => {
                    arr.push(item);
                })
            }
        },
        data() {
            return {
                showTab: 'HitTopics',
                hitTopics: [{
                    title: '搜狐 Q1 财报：营收 3.74 亿美元，同比下滑 8%；净亏损 6800 万美元，较上年同期的净亏损 2100 万美元扩大',
                    info: '搜狐（NASDAQ：SOHU）发布该公司截至2017年3月31日的第一季度未经审计的财报。财报显示，搜狐第一季度营收为3.74亿美元，同比下滑8%；以Non-GAAP计算，归属搜狐的净亏损为6800万美元，稀释后的每股净亏损为1.75美元，搜狐去年同期净亏损为2200万美元。',
                    show: false
                }, {
                    title: 'AcFun 美剧专区疑遭下架 客服称因版权问题整改',
                    info: '近日有网友反映，AcFun美剧几乎全部被下架，连美剧专区都被撤了，大量字幕组翻译的各类美剧也不再更新，网友直呼“最后的净土”遭“沦陷”。就此TechWeb联系AcFun客服后获悉，因涉及版权问题，AcFun相关资源目前正在整改中，具体恢复时间尚未确定。有网友近日称，AcFun首页导航里美剧相关选项好像被撤销了，搜单个剧集名称也无法找到视频资源，用关键词搜美剧也搜不出来。',
                    show: false
                }, {
                    title: '大疆推出如影 2 云台系统 拓展专业影视拍摄市',
                    info: '4月23日，大疆创新在美国广播电视展上，正式发布了新一代的如影2云台系统。如影2云台系统主要面向专业摄影人员，最高负载可以达到达13.6公斤，相比第一代提升了88%，可以轻松承载不同类型的专业的摄影机。同时它采用了更加简化的设计，安装过程轻松快速，并提供了强大的拓展功能，支持相机、监视器等设备连接。',
                    show: false
                }, {
                    title: '经济学人：中国互联网巨头走向全球',
                    info: '《经济学人》杂志本周刊文称，中国互联网行业的“BAT三巨头”，即百度、阿里巴巴和腾讯，正在积极开拓全球市场。腾讯在这场赛跑中处于领先，而阿里巴巴紧随其后。',
                    show: false
                }, {
                    title: '苹果在中国为何走下坡路？',
                    info: '苹果自2009年起开始在中国市场销售iPhone，从此以后便成为了硅谷竞争对手羡慕的对象。谷歌、Facebook和Uber等不是未能进入中国市场，就是在中国市场以“失败”告终。',
                    show: false
                }, {
                    title: '知乎 Live 一年了，它开始支持「七天无理由」退款服务',
                    info: '如果你在进行中的 Live 里听了不超过 15 条语音，觉得不满意，那么 Live 结束后的七天内，你可以无理由退款。',
                    show: false
                }, {
                    title: '「最后一公里」解决了，那共享单车的事故问题呢？',
                    info: '问题虽多，但并非无路可走。',
                    show: false
                }, {
                    title: '短视频第一阵营阵容显形，秒拍、头条视频、快手三国杀，大戏接下来怎么演',
                    info: '自从2013年twitter旗下的vine通过短视频走红之后，国内的秒拍、快手等同类产品也逐渐开始走上风口，但不料在行业认为风口将至之际，突然冒出一个“直播元年”，千播大战彼此血腥厮杀，但整体上却想给短视频来个截胡，然而，随着大批直播网站的',
                    show: false
                }, {
                    title: '马斯克、小扎又多了小伙伴，日本学者用脑电波读取你所思所想 | 潮科技',
                    info: '做掌握技术的人，而不做被技术掌控的人这点很关键。​...',
                    show: false
                }, {
                    title: '港媒消息称众安保险拟第 3 季在港挂牌上',
                    info: '来自港媒消息互联网保险公司众安保险拟提速在港上市，目标第3季挂牌。针对此消息，众安保险对媒体回应称，公司一直有上市计划，但时间和地点未确定。港媒援引众安保险内部人士消息称，公司希望能最快于6月向联交所提交上市申请，并赶及在第3季上市。众安保险于去年已积极筹备在港上市，但去年底一度未有再要求投行就在港上市事宜继续工作，主因当时有意转往A股上市。',
                    show: false
                }, {
                    title: '搜狐 Q1 财报：营收 3.74 亿美元，同比下滑 8%；净亏损 6800 万美元，较上年同期的净亏损 2100 万美元扩大',
                    info: '搜狐（NASDAQ：SOHU）发布该公司截至2017年3月31日的第一季度未经审计的财报。财报显示，搜狐第一季度营收为3.74亿美元，同比下滑8%；以Non-GAAP计算，归属搜狐的净亏损为6800万美元，稀释后的每股净亏损为1.75美元，搜狐去年同期净亏损为2200万美元。',
                    show: false
                }, {
                    title: 'AcFun 美剧专区疑遭下架 客服称因版权问题整改',
                    info: '近日有网友反映，AcFun美剧几乎全部被下架，连美剧专区都被撤了，大量字幕组翻译的各类美剧也不再更新，网友直呼“最后的净土”遭“沦陷”。就此TechWeb联系AcFun客服后获悉，因涉及版权问题，AcFun相关资源目前正在整改中，具体恢复时间尚未确定。有网友近日称，AcFun首页导航里美剧相关选项好像被撤销了，搜单个剧集名称也无法找到视频资源，用关键词搜美剧也搜不出来。',
                    show: false
                }, {
                    title: '大疆推出如影 2 云台系统 拓展专业影视拍摄市',
                    info: '4月23日，大疆创新在美国广播电视展上，正式发布了新一代的如影2云台系统。如影2云台系统主要面向专业摄影人员，最高负载可以达到达13.6公斤，相比第一代提升了88%，可以轻松承载不同类型的专业的摄影机。同时它采用了更加简化的设计，安装过程轻松快速，并提供了强大的拓展功能，支持相机、监视器等设备连接。',
                    show: false
                }, {
                    title: '经济学人：中国互联网巨头走向全球',
                    info: '《经济学人》杂志本周刊文称，中国互联网行业的“BAT三巨头”，即百度、阿里巴巴和腾讯，正在积极开拓全球市场。腾讯在这场赛跑中处于领先，而阿里巴巴紧随其后。',
                    show: false
                }, {
                    title: '苹果在中国为何走下坡路？',
                    info: '苹果自2009年起开始在中国市场销售iPhone，从此以后便成为了硅谷竞争对手羡慕的对象。谷歌、Facebook和Uber等不是未能进入中国市场，就是在中国市场以“失败”告终。',
                    show: false
                }, {
                    title: '知乎 Live 一年了，它开始支持「七天无理由」退款服务',
                    info: '如果你在进行中的 Live 里听了不超过 15 条语音，觉得不满意，那么 Live 结束后的七天内，你可以无理由退款。',
                    show: false
                }, {
                    title: '「最后一公里」解决了，那共享单车的事故问题呢？',
                    info: '问题虽多，但并非无路可走。',
                    show: false
                }, {
                    title: '短视频第一阵营阵容显形，秒拍、头条视频、快手三国杀，大戏接下来怎么演',
                    info: '自从2013年twitter旗下的vine通过短视频走红之后，国内的秒拍、快手等同类产品也逐渐开始走上风口，但不料在行业认为风口将至之际，突然冒出一个“直播元年”，千播大战彼此血腥厮杀，但整体上却想给短视频来个截胡，然而，随着大批直播网站的',
                    show: false
                }, {
                    title: '马斯克、小扎又多了小伙伴，日本学者用脑电波读取你所思所想 | 潮科技',
                    info: '做掌握技术的人，而不做被技术掌控的人这点很关键。​...',
                    show: false
                }, {
                    title: '港媒消息称众安保险拟第 3 季在港挂牌上',
                    info: '来自港媒消息互联网保险公司众安保险拟提速在港上市，目标第3季挂牌。针对此消息，众安保险对媒体回应称，公司一直有上市计划，但时间和地点未确定。港媒援引众安保险内部人士消息称，公司希望能最快于6月向联交所提交上市申请，并赶及在第3季上市。众安保险于去年已积极筹备在港上市，但去年底一度未有再要求投行就在港上市事宜继续工作，主因当时有意转往A股上市。',
                    show: false
                }],
                news: [{
                    title: '蔡文胜放话短期不卖美图股票 儿子却套现 5 亿港',
                    info: '港交所最新披露的信息显示，美图公司（01357.HK）创始人兼主席蔡文胜的儿子 Cai Rongjia 已于4月12日以每股11.86 港元的价格，减持 30 万股，套现约 355.8 万港元。减持后，Cai Rongjia 在美图公司的持股数约 2.54 亿股，持股比例减少至 5.99%，在主要股东中持股数垫底。',
                    show: false
                }, {
                    title: '无人机一周 4 次闯祸:万人滞',
                    info: '衰落，还是瓶颈期？注定是无人机行业无聊的一年？',
                    show: false
                }, {
                    title: '雷军：互联网不打价格战，马云睡觉都在赚',
                    info: '「我说传统商业需要人工的时候，陈总在下面点头，想起卖保险多辛苦，而马云睡觉都可以赚钱。」...',
                    show: false
                }, {
                    title: '中国论文再出丑:责任在谁',
                    info: '4月20日，知名学术出版商施普林格·自然（Springer Nature）一次性撤销旗下杂志《肿瘤生物学》（Tumor  Biology）2012 年至 2016 年发表的来自中国的 107 篇文章，这些文章涉嫌同行评议造假。',
                    show: false
                }, {
                    title: '苹果在中国为何走下坡路？',
                    info: '苹果自2009年起开始在中国市场销售iPhone，从此以后便成为了硅谷竞争对手羡慕的对象。谷歌、Facebook和Uber等不是未能进入中国市场，就是在中国市场以“失败”告终。',
                    show: false
                }, {
                    title: '知乎 Live 一年了，它开始支持「七天无理由」退款服务',
                    info: '如果你在进行中的 Live 里听了不超过 15 条语音，觉得不满意，那么 Live 结束后的七天内，你可以无理由退款。',
                    show: false
                }, {
                    title: '「最后一公里」解决了，那共享单车的事故问题呢？',
                    info: '问题虽多，但并非无路可走。',
                    show: false
                }, {
                    title: '短视频第一阵营阵容显形，秒拍、头条视频、快手三国杀，大戏接下来怎么演',
                    info: '自从2013年twitter旗下的vine通过短视频走红之后，国内的秒拍、快手等同类产品也逐渐开始走上风口，但不料在行业认为风口将至之际，突然冒出一个“直播元年”，千播大战彼此血腥厮杀，但整体上却想给短视频来个截胡，然而，随着大批直播网站的',
                    show: false
                }, {
                    title: 'Quora 融资 8500 万 美元：估值 18 亿美元 向国际扩',
                    info: '成立八年的美国知识问答服务 Quora日前进行了D轮融资，获得了 Collaborative Fund和创业孵化器 Y Combinator领投的 8500 万美元资金。Quora 称，其估值几乎较上轮融资时翻倍，这意味着它的估值目前已经达到约 18 亿美元。在 2014 年的上轮融资中，Quora 的估值为 9 亿美元。',
                    show: false
                }, {
                    title: '百度金融风控负责人王劲离',
                    info: '继百度自动驾驶事业部总经理王劲离职后，另一个负责百度金融风控的同名副总裁王劲也从百度离职。',
                    show: false
                }, {
                    title: '蔡文胜放话短期不卖美图股票 儿子却套现 5 亿港',
                    info: '港交所最新披露的信息显示，美图公司（01357.HK）创始人兼主席蔡文胜的儿子 Cai Rongjia 已于4月12日以每股11.86 港元的价格，减持 30 万股，套现约 355.8 万港元。减持后，Cai Rongjia 在美图公司的持股数约 2.54 亿股，持股比例减少至 5.99%，在主要股东中持股数垫底。',
                    show: false
                }, {
                    title: '无人机一周 4 次闯祸:万人滞',
                    info: '衰落，还是瓶颈期？注定是无人机行业无聊的一年？',
                    show: false
                }, {
                    title: '雷军：互联网不打价格战，马云睡觉都在赚',
                    info: '「我说传统商业需要人工的时候，陈总在下面点头，想起卖保险多辛苦，而马云睡觉都可以赚钱。」...',
                    show: false
                }, {
                    title: '中国论文再出丑:责任在谁',
                    info: '4月20日，知名学术出版商施普林格·自然（Springer Nature）一次性撤销旗下杂志《肿瘤生物学》（Tumor  Biology）2012 年至 2016 年发表的来自中国的 107 篇文章，这些文章涉嫌同行评议造假。',
                    show: false
                }, {
                    title: '苹果在中国为何走下坡路？',
                    info: '苹果自2009年起开始在中国市场销售iPhone，从此以后便成为了硅谷竞争对手羡慕的对象。谷歌、Facebook和Uber等不是未能进入中国市场，就是在中国市场以“失败”告终。',
                    show: false
                }, {
                    title: '知乎 Live 一年了，它开始支持「七天无理由」退款服务',
                    info: '如果你在进行中的 Live 里听了不超过 15 条语音，觉得不满意，那么 Live 结束后的七天内，你可以无理由退款。',
                    show: false
                }, {
                    title: '「最后一公里」解决了，那共享单车的事故问题呢？',
                    info: '问题虽多，但并非无路可走。',
                    show: false
                }, {
                    title: '短视频第一阵营阵容显形，秒拍、头条视频、快手三国杀，大戏接下来怎么演',
                    info: '自从2013年twitter旗下的vine通过短视频走红之后，国内的秒拍、快手等同类产品也逐渐开始走上风口，但不料在行业认为风口将至之际，突然冒出一个“直播元年”，千播大战彼此血腥厮杀，但整体上却想给短视频来个截胡，然而，随着大批直播网站的',
                    show: false
                }, {
                    title: 'Quora 融资 8500 万 美元：估值 18 亿美元 向国际扩',
                    info: '成立八年的美国知识问答服务 Quora日前进行了D轮融资，获得了 Collaborative Fund和创业孵化器 Y Combinator领投的 8500 万美元资金。Quora 称，其估值几乎较上轮融资时翻倍，这意味着它的估值目前已经达到约 18 亿美元。在 2014 年的上轮融资中，Quora 的估值为 9 亿美元。',
                    show: false
                }, {
                    title: '百度金融风控负责人王劲离',
                    info: '继百度自动驾驶事业部总经理王劲离职后，另一个负责百度金融风控的同名副总裁王劲也从百度离职。',
                    show: false
                }]
            }
        }
    }

</script>
<style scoped>
    .layout {
        background-color: #fff;
        z-index: 999;
        top: 0;
        left: 0;
        right: 0;
        box-shadow: none;
    }
    
    h3 {
        margin: 0;
    }
    
    .head {
        margin: 10px 0 10px 15px;
    }
    
    .nav {
        height: 30px;
        background: #607d8b;
    }
    
    .nav-container {
        height: 30px!important;
        overflow: hidden;
    }
    
    .nav a {
        height: 30px;
        line-height: 30px;
        display: block;
        font-size: 14px;
        float: left;
        color: #fff;
        padding: 0 15px;
    }
    
    .nav a.active {
        background: #78909c;
    }
    
    #fixedTools {
        position: fixed;
        right: 40px;
        bottom: 40px;
        border: 1px solid #DDD;
        background: #FFF;
        width: 36px;
        text-align: center;
        border-radius: 2px;
        line-height: 1.25;
        z-index: 1000;
    }
    
    #fixedTools a {
        font-size: 20px;
        padding: 10px;
        display: block;
        color: #999;
        text-decoration: none;
    }
    .hidden {
        display: none;
    }
</style>