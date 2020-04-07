<template>
  <div class="background">
    <div class="page">
      <div class="resume">
        <div class="left-column">
          <div class="headline">
            <div class="headline-name">
              <span>{{ person.name.first }} {{ person.name.middle }}</span>
              <span class="uppercase">{{ person.name.last }}</span>
            </div>

            <p>
              <span class="txt-full-white">{{ person.position }}</span>
              <br />
              <span>{{ person.contact.city }}</span>,
              <span class="uppercase">{{ person.contact.country }}</span>
            </p>
          </div>

          <div class="txt-multiline">{{ person.about }}</div>

          <div class="txt-multiline">{{ person.knowledge }}</div>

          <div class="container container-content contact-container">
            <a
              v-if="person.contact.email"
              :href="contactLinks.email"
              class="container-item external-link"
            >
              <i class="container-icon contact-icon material-icons">mail</i>
              <span class="icon-label txt-full-white">{{ person.contact.email }}</span>
            </a>

            <a
              v-if="person.contact.phone"
              :href="contactLinks.phone"
              class="container-item external-link"
            >
              <i class="container-icon contact-icon material-icons">phone</i>
              <span class="icon-label txt-full-white">{{ person.contact.phone }}</span>
            </a>

            <a
              v-if="person.contact.github"
              :href="contactLinks.github"
              class="container-item external-link"
            >
              <i class="container-icon contact-icon fa fa-github"></i>
              <span class="icon-label txt-full-white">{{ person.contact.github }}</span>
            </a>
          </div>

          <div class="container skills-container">
            <span class="subheadline">Skills</span>
            <div class="container-content skills-content">
              <a
                v-for="(skill, index) in person.skills"
                :key="index"
                class="container-item tem"
                :href="skill.url"
              >
                <i v-if="skill.iconClass" :class="'container-icon skill-icon ' + skill.iconClass"></i>
                <i
                  v-if="skill.materialIcon"
                  class="container-icon skill-icon material-icons"
                >{{ skill.materialIcon }}</i>
                <span class="icon-label">{{ skill.name }}</span>
              </a>
            </div>
          </div>

          <div class="container hobbies-container">
            <span class="subheadline">Hobbies</span>
            <div class="container-content hobbies-content">
              <a
                v-for="(hobby, index) in person.hobbies"
                :key="index"
                class="container-item hobby-item"
                :href="hobby.url"
              >
                <i v-if="hobby.iconClass" :class="'container-icon hobby-icon ' + hobby.iconClass"></i>
                <i
                  v-if="hobby.materialIcon"
                  class="container-icon hobby-icon material-icons"
                >{{ hobby.materialIcon }}</i>
                <span class="icon-label">{{ hobby.name }}</span>
              </a>
            </div>
          </div>
        </div>

        <div class="left-column-bg"></div>

        <div class="right-column">
          <div class="section experience-section">
            <div class="section-headline">
              <i class="section-icon material-icons">work</i>
              <span>Work</span>
            </div>
            <div class="section-content">
              <a
                v-for="(experience, index) of person.experiences"
                :key="index"
                class="section-item"
                :href="experience.website"
              >
                <span class="section-item-header">{{ experience.position }}</span>
                <span class="section-item-subheader">{{ experience.company }}</span>
                <span class="section-item-text">{{ experience.timeperiod }}</span>
                <span class="section-item-text-light">{{ experience.description }}</span>
              </a>
            </div>
          </div>

          <div class="section education-section">
            <div class="section-headline">
              <i class="section-icon material-icons">school</i>
              <span>Education</span>
            </div>
            <div class="section-content">
              <a
                v-for="(education, index) of person.educations"
                :key="index"
                class="section-item"
                :href="education.website"
              >
                <span class="section-item-header">{{ education.degree }}</span>
                <span class="section-item-subheader">{{ education.school }}</span>
                <span class="section-item-text">{{ education.timeperiod }}</span>
                <span class="section-item-text-light">Specialization: {{ education.specialization }}</span>
                <span class="section-item-text-light">GPA: {{ education.gpa }}</span>
              </a>
            </div>
          </div>

          <div class="section projects-section">
            <div class="section-headline">
              <i class="section-icon material-icons">code</i>
              <span>Projects</span>
            </div>
            <div class="section-content">
              <a
                v-for="(project, index) of person.projects"
                :key="index"
                class="section-item"
                :href="project.website"
              >
                <span class="section-item-header">{{ project.name }}</span>
                <span class="section-item-subheader">{{ project.skills }}</span>
                <span class="section-item-text">{{ project.description }}</span>
                <span class="section-item-text-light">{{ project.url }}</span>
              </a>
            </div>
          </div>

          <div class="section contributions-section">
            <div class="section-headline">
              <i class="section-icon fa fa-heart"></i>
              <span>Contributions</span>
            </div>
            <div class="section-content">
              <a
                v-for="(contribution, index) of person.contributions"
                :key="index"
                class="section-item"
                :href="contribution.url"
              >
                <span class="section-item-header">{{ contribution.name }}</span>
                <span class="section-item-subheader">{{ contribution.skills }}</span>
                <span class="section-item-text">{{ contribution.description }}</span>
                <span class="section-item-text-light">{{ contribution.url }}</span>
              </a>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Vue from "vue";
import { importData } from "../data/data.js";

const name = "Resume";
export default Vue.component(name, importData());
</script>


<style lang="less">
@import "../../node_modules/font-awesome/css/font-awesome.css";
@import "../../node_modules/material-design-icons/iconfont/material-icons.css";
@import "../../node_modules/devicons/css/devicons.css";
@import "../../node_modules/roboto-fontface/css/roboto/roboto-fontface.css";

@main-color: #a800fa;

a {
  color: inherit;
  cursor: pointer;
  text-decoration-line: none;

  &:visited {
    color: inherit;
  }
}

.background {
  overflow-x: hidden;
  background: #cccccc;
  margin: 0;
  padding: 0;
  -webkit-print-color-adjust: exact;
  box-sizing: border-box;
}

.page {
  background: white;
  position: relative;
  width: 21cm;
  height: 29.68cm;
  display: block;
  page-break-after: auto;
  overflow: hidden;
}

.material-icons {
  color: @main-color;
  position: relative;
}

.fa {
  color: @main-color;
  position: relative;
}

.section-icon {
  top: 2.5px;
  font-size: 1.4em;
}

.container-icon {
  color: white;
  font-size: 1.3em;
  margin-right: 10px;

  top: 2.5px;
  position: relative;
}

.skill-icon {
  font-size: 1.8em;
}

.contact-icon {
  font-size: 1.5em;
}

.resume {
  display: flex;
  position: relative;

  font-family: "Roboto" !important;
  font-size: 0.9em;
}

.left-column {
  display: block;
  position: absolute;

  width: 30%;
  height: 100%;
  padding: 30px;
  padding-top: 45px;
  text-align: left;

  color: rgba(255, 255, 255, 0.59);
  background-color: @main-color;
  overflow: hidden;
  z-index: 2;

  opacity: 100%;
}

.left-column-bg {
  background-repeat: no-repeat;
  background-size: cover;
  background-position: 25% 25%;

  opacity: 0.4; // up this value to contrast the cover image

  height: 100%;
  width: 35%;
  padding: 30px;
  padding-top: 45px;

  display: block;
  overflow: hidden;
  position: relative;
  top: 0;
  z-index: 1;
}

.right-column {
  display: flex;
  flex-direction: column;
  padding: 30px;
  background: white;

  height: 100%;
  width: 65%;
}

.external-link {
  display: block;
  margin-bottom: 5px;
}

.block-marged {
  margin-top: 15px;
  margin-bottom: 15px;
}

.multi-line-text {
  margin-top: 30px;
  margin-bottom: 20px;
}

.container {
  margin-top: 30px;
  margin-bottom: 30px;
}

.container-content {
  display: flex;
  flex-direction: column;
}

.container-item {
  display: grid;
  grid-template-columns: 30px auto;

  color: rgba(255, 255, 255, 0.6);

  margin-right: 25px;
  margin-bottom: 10px;

  transition: 0.5s;

  &:hover {
    color: rgba(255, 255, 255, 0.8);
    transition: 0.5s;
  }
}

.txt-full-white {
  color: white;
}

.txt-multiline {
  margin-top: 30px;
  margin-bottom: 20px;
}

.subheadline {
  color: rgba(255, 255, 255, 0.8);
  font-size: 1.2em;

  display: block;
  margin-bottom: 10px;
}

.headline-name {
  color: white;
  font-size: 1.3em;
  font-weight: bold;
}

.uppercase {
  text-transform: uppercase;
}

.icon-label {
  top: 2.5px;
  position: relative;
}

.section {
  margin-top: 10px;
  margin-bottom: 10px;
}

.section-headline {
  color: @main-color;
  display: inline-block;
  font-size: 1.3em;
  margin-left: 5px;
}

.section-content {
  margin-top: 10px;
  padding-left: 32px;
}

.section-item {
  display: block;
  margin-bottom: 10px;
}

.section-item-header {
  display: block;
  line-height: 1.5em;

  font-size: 1.1em;
  font-weight: 500;
}

.section-item-subheader {
  display: block;
  line-height: 1.5em;

  font-weight: 400;
}

.section-item-text {
  display: block;
  line-height: 1.5em;

  font-weight: 300;
}

.section-item-text-light {
  display: block;
  color: rgba(0, 0, 0, 0.42);

  font-size: 14px;
  font-weight: 300;
}
</style>