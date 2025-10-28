<template>
  <v-app>
    <!-- 主要内容区域 -->
    <v-main>
      <!-- 欢迎区域 -->
      <section id="home" class="hero-section">
        <v-container fluid class="fill-height">
          <v-row align="center" justify="center">
            <v-col cols="12" md="8" class="text-center">
              <h1 class="text-h2 font-weight-bold mb-4">欢迎来到 Yule.ink</h1>
              <p class="text-h5 mb-6">这个页面会带你了解我</p>
              <p class="text-body-1 mb-8 max-width-600 mx-auto">
                总感觉这里少了点什么... 算了，那就随便写点
              </p>
              <v-btn
                color="primary"
                size="large"
                class="mr-4"
                @click="scrollToSection('projects')"
              >
                玩玩具
                <v-icon end>mdi-arrow-right</v-icon>
              </v-btn>
              <v-btn
                color="secondary"
                size="large"
                variant="outlined"
                @click="scrollToSection('contact')"
              >
                和我玩
                <v-icon end>mdi-email</v-icon>
              </v-btn>
            </v-col>
          </v-row>
        </v-container>
      </section>

      <!-- 关于我区域 -->
      <section id="about" class="section-padding">
        <v-container>
          <v-row>
            <v-col cols="12" class="text-center mb-8">
              <h2 class="text-h3 font-weight-bold">关于我</h2>
              <v-divider class="my-4 mx-auto" width="100"></v-divider>
              <p class="text-body-1 mt-4">人猫二象性</p>
            </v-col>
          </v-row>
          <v-row align="center">
            <v-col cols="12" md="12">
              <v-card elevation="4">
                <v-card-text class="pa-6">
                  <h3 class="text-h5 mb-4">Yule 的设定</h3>
                  <p class="mb-4">Yule 可能是 Yule 或者 Yule 家里的小猫</p>
                  <p class="mb-4">如果小猫发表了一些暴论，请你原谅他喵~</p>
                  <p>Yule 是个家里蹲，除了世界毁灭以外，一般不会轻易出门</p>
                </v-card-text>
              </v-card>
            </v-col>
          </v-row>
        </v-container>
      </section>

      <!-- 作品展示区域 -->
      <section id="projects" class="section-padding">
        <v-container>
          <v-row>
            <v-col cols="12" class="text-center mb-8">
              <h2 class="text-h3 font-weight-bold">Yule 的小玩具</h2>
              <v-divider class="my-4 mx-auto" width="100"></v-divider>
              <p class="text-body-1 mt-4">好像是他自己捣鼓的?</p>
            </v-col>
          </v-row>
          <v-row>
            <v-col
              cols="12"
              md="6"
              lg="4"
              v-for="project in projects"
              :key="project.name"
            >
              <v-card elevation="4" class="project-card">
                <v-card-title class="pb-2">
                  {{ project.name }}
                </v-card-title>
                <v-card-text>
                  <p class="text-body-2 mb-3">{{ project.description }}</p>
                  <v-chip
                    v-for="tech in project.technologies"
                    :key="tech"
                    class="ma-1"
                    size="small"
                    color="secondary"
                    variant="tonal"
                  >
                    {{ tech }}
                  </v-chip>
                </v-card-text>
                <v-card-actions>
                  <v-btn
                    color="primary"
                    variant="text"
                    :href="project.githubUrl"
                    target="_blank"
                  >
                    <v-icon start>mdi-github</v-icon>
                  </v-btn>
                  <v-btn
                    v-if="project.demoUrl"
                    color="secondary"
                    variant="text"
                    :href="project.demoUrl"
                    target="_blank"
                  >
                    <v-icon start>mdi-open-in-new</v-icon>
                  </v-btn>
                </v-card-actions>
              </v-card>
            </v-col>
          </v-row>
        </v-container>
      </section>

      <!-- 联系区域 -->
      <section id="contact" class="section-padding bg-primary text-white">
        <v-container>
          <v-row>
            <v-col cols="12" class="text-center mb-8">
              <h2 class="text-h3 font-weight-bold">联系我</h2>
              <v-divider
                class="my-4 mx-auto"
                width="100"
                color="white"
              ></v-divider>
            </v-col>
          </v-row>
          <v-row justify="center">
            <v-col cols="12" md="8" class="text-center">
              <p class="text-h6 mb-6">
                有兴趣合作或者想要了解更多？欢迎与我联系！
              </p>
              <div class="d-flex justify-center flex-wrap">
                <v-btn
                  color="white"
                  variant="outlined"
                  class="ma-2"
                  href="mailto:yule-best@outlook.com"
                >
                  <v-icon start>mdi-email</v-icon>
                  yule-best@outlook.com
                </v-btn>
                <v-btn
                  color="white"
                  variant="outlined"
                  class="ma-2"
                  href="https://github.com/YuleBest"
                  target="_blank"
                >
                  <v-icon start>mdi-github</v-icon>
                  YuleBest
                </v-btn>
              </div>
            </v-col>
          </v-row>
        </v-container>
      </section>
    </v-main>
  </v-app>
</template>

<script setup>
import { ref } from "vue";

// 侧边栏状态
const drawer = ref(false);

// GitHub项目数据
const projects = ref([
  {
    name: "xiaomi-bl-unlock-helper",
    description:
      "小米 BL 解锁答题助手丨一款面向小米手机用户的客户端 Web 应用，助你备考小米解锁 Bootloader 考试，应用支持智能题库搜索、收藏管理和解锁资格计算，且支持离线运行。",
    technologies: ["JavaScript", "HTML5"],
    githubUrl: "https://github.com/YuleBest/xiaomi-bl-unlock-helper",
    demoUrl: "bl.yule.ink",
  },
  {
    name: "gobangol",
    description:
      "Gobang OL 是一个基于 Web 的在线五子棋对战游戏平台，采用现代化的前端技术栈开发，提供流畅的游戏体验和优雅的用户界面。项目支持实时对战、游戏记录、用户设置等功能，旨在为用户提供一个简洁而功能完善的在线五子棋游戏体验。",
    technologies: ["Vue", "Vuetify", "TypeScript"],
    githubUrl: "https://github.com/YuleBest/gobangol",
    demoUrl: "https://gobangol.yule.ink",
  },
  {
    name: "YulesBlog",
    description: "Yule 的博客",
    technologies: [],
    githubUrl: "https://github.com/YuleBest/YulesBlog",
    demoUrl: "https://blog.yule.ink",
  },
]);

// 滚动到指定区域
const scrollToSection = (sectionId) => {
  const element = document.getElementById(sectionId);
  if (element) {
    element.scrollIntoView({ behavior: "smooth" });
  }
  drawer.value = false; // 关闭侧边栏
};
</script>

<style scoped>
.hero-section {
  min-height: 100vh;
  display: flex;
  align-items: center;
}

.section-padding {
  padding: 80px 0;
}

.max-width-600 {
  max-width: 600px;
}

.skill-card {
  height: 100%;
  transition: transform 0.3s ease, box-shadow 0.3s ease;
}

.skill-card:hover {
  transform: translateY(-5px);
  box-shadow: 0 8px 25px rgba(0, 0, 0, 0.15);
}

.project-card {
  height: 100%;
  transition: transform 0.3s ease, box-shadow 0.3s ease;
}

.project-card:hover {
  transform: translateY(-5px);
  box-shadow: 0 8px 25px rgba(0, 0, 0, 0.15);
}

/* 响应式设计 */
@media (max-width: 768px) {
  .hero-section {
    padding: 40px 0;
  }

  .section-padding {
    padding: 60px 0;
  }

  .text-h2 {
    font-size: 2rem !important;
  }

  .text-h5 {
    font-size: 1.25rem !important;
  }
}

/* 滚动动画效果 */
@media (prefers-reduced-motion: no-preference) {
  .skill-card,
  .project-card {
    animation: fadeInUp 0.6s ease-out;
  }
}
</style>
