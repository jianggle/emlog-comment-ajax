emlog友链分类管理，基于emlog5.3.1，使用说明：http://www.eqifei.net/post-465.html

## 前端代码示例：

var data={
	comname: $("#comname").val(),
	comment: $("#comment").val(),
	commail: $("#commail").val(),
	comurl: $("#comurl").val(),
	imgcode: $("input[name=imgcode]").val(),
	gid: $("#comment-gid").val(),
	pid: $("#comment-pid").val()
};
$.ajax({
	url: 'index.php?action=addcom',
	type: 'post',
	dataType: 'json',
	data: data,
	success: function(data){
		var tip = $("#commentTips");
		switch(data.status){
			case "1":
				tip.text("主人已关闭此篇文章的评论功能啦！");
				break;
			case "2":
				tip.text("已存在相同内容评论啦！");
				break;
			case "3":
				tip.text("您提交评论的速度太快了，请稍后再发表评论吧！");
				break;
			case "4":
				tip.text("请填写昵称哦！");
				break;
			case "5":
				tip.text("昵称不超过6个汉字或者20个字符哦！");
				break;
			case "6":
				tip.text("请填写正确的邮件地址哦！");
				break;
			case "7":
				tip.text("不能使用管理员昵称或邮箱评论哦！");
				break;
			case "8":
				tip.text("主页地址不符合规范哦！");
				break;
			case "9":
				tip.text("请填写评论内容哦！");
				break;
			case "10":
				tip.text("评论内容超出最大字数限制了哦！");
				break;
			case "11":
				tip.text("评论内容需包含中文哦！");
				break;
			case "12":
				tip.text("验证码不对哒！");
				break;
			case "13":
				alert("评论发表成功！");
				location.reload();
				break;
			case "14":
				alert("评论发表成功，请等待管理员审核吧！");
				location.reload();
				break;
		}
	}
});