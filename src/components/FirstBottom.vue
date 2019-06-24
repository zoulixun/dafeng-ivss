<template>
    <div class="firstBottom">
        <div class="firstShop">
            <div id="firstChart"></div>
        </div>
        <div class="secondShop">
            <div id="secondChart"></div>
        </div>
        <div class="thirdShop">
            <div id="thirdChart"></div>
        </div>
    </div> 
</template>
<script>
export default {
    name:'FirstBottom',
    data(){
        return{
            shopRate:{"firstShopRate":50,"secondShopRate":90,"thirdShopRate":100},
	        currentProcess:{
                "firstShop": {"plan": 10, "actual": 9},
                "secondShop":{"plan": 5, "actual": 5},
                "thirdShop": {"plan": 6, "actual": 1}
            },
	        runRate:{
                "firstShop": {"run": 10, "stop": 9,"yearRate": 98, "weekRate": 96},
                "secondShop":{"run": 20, "stop": 1,"yearRate": 99, "weekRate": 99},
                "thirdShop": {"run": 15, "stop": 2,"yearRate": 94, "weekRate": 95}
            }
        }
    },
    mounted(){
        this.drawFirstShop();
        this.drawSecondShop();
        this.drawThirdShop();
    },
    methods:{
        drawFirstShop(){
        // 基于准备好的dom，初始化echarts实例
        let firstChart = this.$echarts.init(document.getElementById('firstChart'));
        var firstOption = {
            title : {
		        text: '一车间',
		        x:'center',
		        y:10,
		        textStyle:{
		        	color:'#fff',
		        	fontSize:25
		        }
		    },
            tooltip : {
                formatter: "{a} <br/>{b} : {c}%"
            },
            series : [
                {
                    name:'工作进度',
                    type:'gauge',
                    startAngle: 180,
                    itemStyle:{
                        color: 'rgba(255,255,255,0.6)',
                        
	                },
                    endAngle: 0,
                    center : ['50%', '90%'],    // 默认全局居中
                    radius : 95,
                    axisLine: {            // 坐标轴线
                        lineStyle: {       // 属性lineStyle控制线条样式
                            color: [[0.09, 'lime'],[0.82, '#1e90ff'],[1, '#ff4500']],
                            width: 3,
                            shadowColor : '#fff', //默认透明
                            shadowBlur: 10
                        }
                    },
                    axisTick: {            // 坐标轴小标记
                        splitNumber: 5,   // 每份split细分多少段
                        length :12,        // 属性length控制线长
                    },
                    axisLabel: {           // 坐标轴文本标签，详见axis.axisLabel
                        formatter: function(v){
                            switch (v+''){
                                case '10': return '低';
                                case '50': return '';
                                case '90': return '高';
                                default: return '';
                            }
                        },
                        textStyle: {       // 其余属性默认使用全局文本样式，详见TEXTSTYLE
                            color: '#fff',
                            fontSize: 15,
                            fontWeight: 'bolder'
                        }
                    },
                    pointer: {
                        width:8,
                        length: '80%',
                        color: 'rgba(255, 255, 255, 0.8)'
                    },
                    title : {
                        show : true,
                        offsetCenter: [0, '-60%'],       // x, y，单位px
                        textStyle: {       // 其余属性默认使用全局文本样式，详见TEXTSTYLE
                            color: '#fff',
                            fontSize: 15
                        }
                    },
                    detail : {
                        show : true,
                        backgroundColor: 'rgba(0,0,0,0)',
                        borderWidth: 0,
                        borderColor: 'red',
                        width: 80,
                        height: 30,
                        offsetCenter: [0, -30],       // x, y，单位px
                        formatter:'{value}%',
                        textStyle: {       // 其余属性默认使用全局文本样式，详见TEXTSTYLE
                            fontSize : 25,
                            color:'#fff'
                        }
                    },
                    data:[{value: this.shopRate.firstShopRate, name: '按时完工率'}]
                }
            ]};       
        // 绘制图表
        firstChart.setOption(firstOption);
        },
        drawSecondShop(){
             // 基于准备好的dom，初始化echarts实例
        let secondChart = this.$echarts.init(document.getElementById('secondChart'));
        var secondOption = {
            title : {
		        text: '二车间',
		        x:'center',
		        y:10,
		        textStyle:{
		        	color:'#fff',
		        	fontSize:25
		        }
		    },
            tooltip : {
                formatter: "{a} <br/>{b} : {c}%"
            },
            series : [
                {
                    name:'业务指标',
                    type:'gauge',
                    startAngle: 180,
                    itemStyle:{
                        color: 'rgba(255,255,255,0.6)',
                        
	                },
                    endAngle: 0,
                    center : ['50%', '90%'],    // 默认全局居中
                    radius : 95,
                     axisLine: {            // 坐标轴线
                        lineStyle: {       // 属性lineStyle控制线条样式
                            color: [[0.09, 'lime'],[0.82, '#1e90ff'],[1, '#ff4500']],
                            width: 3,
                            shadowColor : '#fff', //默认透明
                            shadowBlur: 10
                        }
                    },
                    axisTick: {            // 坐标轴小标记
                        splitNumber: 5,   // 每份split细分多少段
                        length :12,        // 属性length控制线长
                    },
                    axisLabel: {           // 坐标轴文本标签，详见axis.axisLabel
                        formatter: function(v){
                            switch (v+''){
                                case '10': return '低';
                                case '50': return '';
                                case '90': return '高';
                                default: return '';
                            }
                        },
                        textStyle: {       // 其余属性默认使用全局文本样式，详见TEXTSTYLE
                            color: '#fff',
                            fontSize: 15,
                            fontWeight: 'bolder'
                        }
                    },
                    pointer: {
                        width:8,
                        length: '80%',
                        color: 'rgba(255, 255, 255, 0.8)'
                    },
                    title : {
                        show : true,
                        offsetCenter: [0, '-60%'],       // x, y，单位px
                        textStyle: {       // 其余属性默认使用全局文本样式，详见TEXTSTYLE
                            color: '#fff',
                            fontSize: 15
                        }
                    },
                    detail : {
                        show : true,
                        backgroundColor: 'rgba(0,0,0,0)',
                        borderWidth: 0,
                        borderColor: 'red',
                        width: 80,
                        height: 30,
                        offsetCenter: [0, -30],       // x, y，单位px
                        formatter:'{value}%',
                        textStyle: {       // 其余属性默认使用全局文本样式，详见TEXTSTYLE
                            fontSize : 25,
                            color:'#fff'
                        }
                    },
                    data:[{value: this.shopRate.secondShopRate, name: '按时完工率'}]
                }
            ]};       
        // 绘制图表
        secondChart.setOption(secondOption);
        },
        drawThirdShop(){
             // 基于准备好的dom，初始化echarts实例
        let thirdChart = this.$echarts.init(document.getElementById('thirdChart'));
        var thirdOption = {
            title : {
		        text: '三车间',
		        x:'center',
		        y:10,
		        textStyle:{
		        	color:'#fff',
		        	fontSize:25
		        }
		    },
            tooltip : {
                formatter: "{a} <br/>{b} : {c}%"
            },
            series : [
                {
                    name:'业务指标',
                    type:'gauge',
                    startAngle: 180,
                    itemStyle:{
                        color: 'rgba(255,255,255,0.6)',
                        
	                },
                    endAngle: 0,
                    center : ['50%', '90%'],    // 默认全局居中
                    radius : 95,
                     axisLine: {            // 坐标轴线
                        lineStyle: {       // 属性lineStyle控制线条样式
                            color: [[0.09, 'lime'],[0.82, '#1e90ff'],[1, '#ff4500']],
                            width: 3,
                            shadowColor : '#fff', //默认透明
                            shadowBlur: 10
                        }
                    },
                    axisTick: {            // 坐标轴小标记
                        splitNumber: 5,   // 每份split细分多少段
                        length :12,        // 属性length控制线长
                    },
                    axisLabel: {           // 坐标轴文本标签，详见axis.axisLabel
                        formatter: function(v){
                            switch (v+''){
                                case '10': return '低';
                                case '50': return '';
                                case '90': return '高';
                                default: return '';
                            }
                        },
                        textStyle: {       // 其余属性默认使用全局文本样式，详见TEXTSTYLE
                            color: '#fff',
                            fontSize: 15,
                            fontWeight: 'bolder'
                        }
                    },
                    pointer: {
                        width:8,
                        length: '80%',
                        color: 'rgba(255, 255, 255, 0.8)'
                    },
                    title : {
                        show : true,
                        offsetCenter: [0, '-60%'],       // x, y，单位px
                        textStyle: {       // 其余属性默认使用全局文本样式，详见TEXTSTYLE
                            color: '#fff',
                            fontSize: 15
                        }
                    },
                    detail : {
                        show : true,
                        backgroundColor: 'rgba(0,0,0,0)',
                        borderWidth: 0,
                        borderColor: 'red',
                        width: 80,
                        height: 30,
                        offsetCenter: [0, -30],       // x, y，单位px
                        formatter:'{value}%',
                        textStyle: {       // 其余属性默认使用全局文本样式，详见TEXTSTYLE
                            fontSize : 25,
                            color:'#fff'
                        }
                    },
                    data:[{value: this.shopRate.thirdShopRate, name: '按时完工率'}]
                }
            ]};       
        // 绘制图表
        thirdChart.setOption(thirdOption);
        }

    }
}
</script>
<style scoped>
 .firstBottom{
    width: 100%;
    text-align: center;
    position: relative;
    margin-left: 25px;   
}
.firstShop{
    float: left;
    width: 30%;
    height:260px;
    border: 1px rgba(238, 238, 238, 0.4)  solid;
    border-radius: 5px;
    background: rgba(0, 0, 102, 0.2) ;
    margin-top: 5px; 
}
.secondShop{
    float: left;
    width: 30%;
    height:260px;
    border: 1px rgba(238, 238, 238, 0.4)  solid;
    border-radius: 5px;
    background: rgba(0, 0, 102, 0.2);
    margin-left: 2px;
     margin-top: 5px; 
}
.thirdShop{
    float: left;
    width: 30%;
    height:260px;
    border: 1px rgba(238, 238, 238, 0.4)  solid;
    border-radius: 5px;
    background: rgba(0, 0, 102, 0.2);
    margin-left: 2px;
     margin-top: 5px; 
}
#firstChart{
    display: inline-block;
    width: 200px;
    height: 200px;
}
#secondChart{
    display: inline-block;
    width: 200px;
    height: 200px;
}
#thirdChart{
    display: inline-block;
    width: 200px;
    height: 200px;
}
</style>

