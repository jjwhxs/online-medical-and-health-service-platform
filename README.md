### 系统介绍

基于SpringBoot实现的在线医疗健康服务平台采用前后端一体化的架构方式，前台系统实现了用户注册/登录、网站首页、医院简介、患者服务、就医指南、通知公告等功能模块，患者可以在后台系统中进行挂号、缴费、取药、查询、病史等操作，管理员可以在后台系统中进行医生管理、患者管理、药品管理、疾病管理、预约管理、病史管理、住院信息管理等操作。

### 技术选型

开发工具：idea2020.3

运行环境：jdk1.8+maven3.6.0+MySQL5.7

服务端技术：Springboot+Mybatis-Plus+SpringSecurity+Fastjson

前端技术：html+css+javascript+freemarker

### 成果展示

用户注册/登录
<img width="1877" height="1034" alt="用户注册登录" src="https://github.com/user-attachments/assets/77919d96-a83c-42b6-8166-aefb54921e95" />

前台系统->网站首页
<img width="1882" height="1037" alt="前台系统-网站首页" src="https://github.com/user-attachments/assets/ffe494bb-236e-444b-8190-a9133bd6bc77" />

前台系统->医院简介
<img width="1879" height="1032" alt="前台系统-医院简介" src="https://github.com/user-attachments/assets/c27a779a-3ae1-40fc-9415-092796c1f9c1" />

前台系统->患者服务
<img width="1880" height="1035" alt="前台系统-患者服务" src="https://github.com/user-attachments/assets/4b5aaec1-ac4b-4e8a-863d-99c9f05ae1ba" />

前台系统->就医指南
<img width="1881" height="1034" alt="前台系统-就医指南" src="https://github.com/user-attachments/assets/fbdb8ba6-efe1-4def-89f1-89a9c0cb72ef" />

前台系统->通知公告
<img width="1876" height="941" alt="前台系统-通知公告" src="https://github.com/user-attachments/assets/9ba9cd5e-1340-4b5b-bb1b-f7a01207e9d8" />

患者登录后操作后台系统
<img width="1881" height="1034" alt="患者登录后操作后台系统" src="https://github.com/user-attachments/assets/db5f69ff-1c1c-4907-89bd-e548cdbe1b51" />

后台系统->医生管理
<img width="1910" height="1045" alt="后台系统-医生管理" src="https://github.com/user-attachments/assets/b967ab4b-0295-4ede-80be-931b464cf7dc" />

后台系统->预约管理
<img width="1910" height="1045" alt="后台系统-预约管理" src="https://github.com/user-attachments/assets/3c7245da-55c3-4328-841b-185365906e8b" />

后台系统->病史管理
<img width="1910" height="1045" alt="后台系统-病史管理" src="https://github.com/user-attachments/assets/e7d3e397-c50c-4d88-b5bb-3e9b5719b7ef" />

后台系统->住院信息管理
<img width="1910" height="1045" alt="后台系统-住院信息管理" src="https://github.com/user-attachments/assets/8f8c235b-27bb-4004-9e9d-23298f57569b" />

### 源码展示

@Controller

public class DrugsController {

@Autowired

DrugsService drugsService;

@RequestMapping("admin/drugsManage")

public String drugsManage(HttpServletRequest request, @RequestParam(value = "name", required = false) String name, @RequestParam(value = "type", required = false) Integer type) {

    request.setAttribute("name", name);
    Drugs drugs = new Drugs();
    drugs.setName(name);
    drugs.setType(type);
    request.setAttribute("drugs", drugsService.getAllDrugs(drugs));
    return "/admin/drugsManage";
    
}

@RequestMapping(value = "/admin/drug/{id}", method = RequestMethod.DELETE)

@ResponseBody

public JSONObject delDrug(@PathVariable Integer id) {

    JSONObject json = new JSONObject();
    json.put("message", drugsService.delDrug(id));
    return json;
    
}

@RequestMapping(value = "/admin/drug", method = RequestMethod.POST)

@ResponseBody

public JSONObject addDrug(@RequestBody Drugs drugs) {

    JSONObject json = new JSONObject();
    json.put("message", drugsService.addDrug(drugs));
    return json;
    
}

@RequestMapping("/admin/drugAdd")

public String drugAddPage() {

    return "/admin/add/drugadd";
    
}

@RequestMapping(value = "/admin/drug/{id}", method = RequestMethod.GET)

public String drugInfo(HttpServletRequest request, @PathVariable Integer id) {

    request.setAttribute("drug", drugsService.getDrug(id));
    return "/admin/info/drugsinfo";
    
}

@RequestMapping(value = "/admin/drug", method = RequestMethod.PUT)

@ResponseBody

public JSONObject updateDrug(@RequestBody Drugs drugs) {

    JSONObject json = new JSONObject();
    json.put("message", drugsService.updateDrug(drugs));
    return json;
    
}

}

### 账号地址及其它说明

1、地址说明

访问链接：localhost:8181/hospital/

2、账号说明

患者：rouse/123456

管理员：admin/123456

3、目录结构展示

<img width="980" height="174" alt="目录结构展示" src="https://github.com/user-attachments/assets/5cb2f09b-2bbb-4e43-8bb3-5593d60ea863" />

4、项目结构展示

<img width="1727" height="889" alt="项目结构展示" src="https://github.com/user-attachments/assets/427a3f32-0caa-46b1-8b9f-b7a6119dbead" />

5、运行步骤

1）创建数据库、导入sql脚本

2）修改application.yaml中的数据库配置文件，启动服务端，访问链接

### 获取方式(可远程调试)
访问链接(在浏览器中手动输入下图中的地址)：

<img width="1054" height="131" alt="链接" src="https://github.com/user-attachments/assets/7f7d69f6-4ae1-4235-be59-3b5e19370ab0" />

若资源获取失败，可添加happy35596339(vx)或2061772307(qq)进行交流
