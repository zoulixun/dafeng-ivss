<template>
    <div class="firstTop">
        <div class="leftItem">
            <div id="leftEchart"></div>
        </div>
        <div class="rightItem">
                <div class="rightFirst">
                    <div class="shopName">一车间</div>
                    <div class="done">运行</div>
                    <div class="doneAmount">{{runRate.firstShop.run}}</div>
                    <div class="stop">停机</div>
                    <div class="stopAmount">{{runRate.firstShop.stop}}</div>
                    <div class="yearRateTitle">年开机率</div>
                    <div class="yearrate">{{runRate.firstShop.yearRate}}</div>
                    <div class="weekRateTitle">周开机率</div>
                    <div class="weekrate">{{runRate.firstShop.weekRate}}</div>
                </div>
                <div class="rightSecond">
                    <div class="shopName">一车间</div>
                    <div class="done">运行</div>
                    <div class="doneAmount">{{runRate.secondShop.run}}</div>
                    <div class="stop">停机</div>
                    <div class="stopAmount">{{runRate.secondShop.stop}}</div>
                    <div class="yearRateTitle">年开机率</div>
                    <div class="yearrate">{{runRate.secondShop.yearRate}}</div>
                    <div class="weekRateTitle">周开机率</div>
                    <div class="weekrate">{{runRate.secondShop.weekRate}}</div>
                </div>
                <div class="rightThird">
                    <div class="shopName">一车间</div>
                    <div class="done">运行</div>
                    <div class="doneAmount">{{runRate.thirdShop.run}}</div>
                    <div class="stop">停机</div>
                    <div class="stopAmount">{{runRate.thirdShop.stop}}</div>
                    <div class="yearRateTitle">年开机率</div>
                    <div class="yearrate">{{runRate.thirdShop.yearRate}}</div>
                    <div class="weekRateTitle">周开机率</div>
                    <div class="weekrate">{{runRate.thirdShop.weekRate}}</div>
                </div>
        </div>
    </div>  

</template>
<script>

export default {
    name:'FirstTop',
    data(){
        return{
            shopRate:{"firstShopRate":50,"secondShopRate":90,"thirdShopRate":100},
	        currentProcess:{
                "firstShop": {"plan": 10, "actual": 9},
                "secondShop":{"plan": 5, "actual": 5},
                "thirdShop": {"plan": 6, "actual": 1}
            },
	        runRate:{
                "firstShop": {"run": 10, "stop": 9,"yearRate": "98%", "weekRate": "96%"},
                "secondShop":{"run": 20, "stop": 1,"yearRate": "97%", "weekRate": "99%"},
                "thirdShop": {"run": 15, "stop": 2,"yearRate": "96%", "weekRate": "96%"}
            }
        }
    },
    mounted(){
        this.drawLeftEcahrt();
    },
    methods:{
        drawLeftEcahrt(){
            let leftEchart = this.$echarts.init(document.getElementById('leftEchart'));
            var option_workshop = {
            title : {
		        text: '当日计划完成情况',
		        x:30,
		        y:10,
		        textStyle:{
		        	color:'#fff',
		        	fontSize:25
		        }
		    },
	            grid:{
	                x:50                   
	            },
	            legend: {
	            	x:320,
                    y:10,
                    textStyle: {
                         color: '#fff'
                    }		                	
	            },
	            tooltip: {},
	            dataset: {
	                // 这里指定了维度名的顺序，从而可以利用默认的维度到坐标轴的映射。
	                // 如果不指定 dimensions，也可以通过指定 series.encode 完成映射，参见后文。
	                dimensions: ['product', '计划', '实际'],
	                source: [
	                    {product: '一车间', '计划': this.currentProcess.firstShop.plan, '实际':this.currentProcess.firstShop.actual},
	                    {product: '二车间', '计划': this.currentProcess.firstShop.plan, '实际': this.currentProcess.firstShop.actual},
	                    {product: '三车间', '计划': this.currentProcess.firstShop.plan, '实际': this.currentProcess.firstShop.actual}
	                ]
	            },
	            xAxis: {
	            	type: 'category',
	            	axisLine: {
    	                show: false
    	            },
    	            axisLabel: {
    	                show: true,
    	                 textStyle: {
    	                   color: '#fff',  //更改坐标轴文字颜色	    	                   
    	                 }
    	              },
    	            axisTick:{
    	            	show: false		   //显示/隐藏刻度
    	            }	            	
	            },
	            yAxis: {
	            	axisLine: {
    	                show: false
    	            },
    	            axisLabel: {
    	                show: true,
    	                 textStyle: {
    	                   color: '#fff',  //更改坐标轴文字颜色	    	                   
    	                 }
    	              },
    	            axisTick:{
    	            	show: false		   //显示/隐藏刻度
    	            },
	            },
	            series: [
	            	{
                        type: 'bar',
                        barWidth:25,
					    itemStyle: {
					        normal: {
					        	color:'#cf1322',
					            label: {
					                show: true,
					                position: 'top',
					                textStyle: {
					                    color: '#fff'
					                }
					            }
					        }
					    }
	                },
	                {
                        type: 'bar',
                        barWidth:25,
					    itemStyle: {
					        normal: {
					        	color:'#fadb14',
					            label: {
					                show: true,
					                position: 'top',
					                textStyle: {
					                    color: '#fff'
					                }
					            }
					        }
					    }
	                }
	            ]	           
             };
              leftEchart.setOption(option_workshop);
        }
    }
}
</script>
<style scoped>
.firstTop{
    width: 100%;
    text-align: center; 
    margin-left: 25px;   
}
.leftItem{
    /* display: inline-block; */
    float: left;
    width: 60%;
    height:240px;
    border: 1px rgba(238, 238, 238, 0.4)  solid;
    border-radius: 5px;
    background: rgba(0, 0, 102, 0.2)
}
.rightItem{
    float: left;
    width: 32%;
    height:240px;
    color:#fff;
    border: 1px rgba(0, 0, 0, 0)  solid; 
    border-radius: 5px; 
    background: rgba(0, 0, 102, 0.2)  
}
.rightFirst,.rightSecond,.rightThird{
    float: left;
    width: 30%;
    height:240px;
    border: 1px rgba(238, 238, 238, 0.4)  solid;
    border-radius: 5px;
    background: rgba(0, 0, 102, 0.2)
}
.rightFirst{
    margin-left: 5px;;
} 
.rightSecond{
    margin-left: 5px;
}
.rightThird{
    margin-left: 5px;
}
#leftEchart{
    width: 500px;
    height: 250px;
}
.shopName{
    margin-top: 10px;
}
.done,.doneAmount,.stop,.stopAmount,.yearRateTitle,.yearrate,.weekRateTitle,.weekrate{
    margin-top: 5px;
}
.done{
    color: #7cb305;
}
.stop{
    color: #cf1322;
}
.yearRateTitle,.weekRateTitle{
    color: #fadb14;
}
.doneAmount,.stopAmount,.yearrate,.weekrate{
    font-weight: bold;
}
</style>

