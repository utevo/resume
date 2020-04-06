<template>
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
          <span>{{ person.contact.city }}</span>, <span class="uppercase">{{ person.contact.country }}</span>
        </p>
      </div>

      <div class="txt-multiline">{{ person.about }}</div>

      <div class="txt-multiline">{{ person.knowledge }}</div>

      <div class="contact-container">
        <a v-if="person.contact.email" :href="contactLinks.email" class="container-item external-link">
          <i class="container-icon contact-icon material-icons">mail</i>
          <span class="icon-label block-marged txt-full-white">{{ person.contact.email }}</span>
        </a>

        <a v-if="person.contact.phone" :href="contactLinks.phone" class="container-item external-link">
          <i class="container-icon contact-icon material-icons">phone</i>
          <span class="icon-label block-marged txt-full-white">{{ person.contact.phone }}</span>
        </a>

        <a v-if="person.contact.github" :href="contactLinks.github" class="container-item external-link">
          <i class="container-icon contact-icon fa fa-github"></i>
          <span class="icon-label block-marged txt-full-white">{{ person.contact.github }}</span>
        </a>
      </div>

      <div class="skills-container">
        <span class="subheadline">Skills</span>
        <a
          v-for="(skill, index) in person.skills"
          :key="index"
          class="container-item skill-item"
          :href="skill.url"
        >
          <i v-if="skill.iconClass" :class="'container-icon skill-icon ' + skill.iconClass"></i>
          <i v-if="skill.materialIcon" class="container-icon skill-icon material-icons">{{ skill.materialIcon }}</i>
          <span class="icon-label block-marged">{{ skill.name }}</span>
        </a>
      </div>

      <div class="hobbies-container">
        <span class="subheadline">Hobbies</span>
        <a
          v-for="(hobby, index) in person.hobbies"
          :key="index"
          class="container-item hobby-item"
          :href="hobby.url"
        >
          <i v-if="hobby.iconClass" :class="'container-icon hobby-icon ' + hobby.iconClass"></i>
          <i v-if="hobby.materialIcon" class="container-icon hobby-icon material-icons">{{ hobby.materialIcon }}</i>
          <span class="icon-label block-marged">{{ hobby.name }}</span>
        </a>
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
            <span class="section-item-text">{{ experience.timeperoid }}</span>
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
            <span class="section-item-text">{{ education.timeperoid }}</span>
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

@main-color: #A800FA;


a {
  color: inherit;
  cursor: pointer;
  text-decoration-line: none;

  &:visited {
    color: inherit;
  }
};

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
  font-size: 1.5em;
  margin-right: 10px;

  top: 2px;
  position: relative;
}

.resume {
  display: flex;
  position: relative;

  font-family: 'Roboto' !important;
  font-size: 0.9em;
}

.left-column {
  display: block;
  position: absolute;

  width: 30%;
  height: 200%;
  padding: 30px;
  padding-top: 45px;
  text-align: left;

  color:rgba(255,255,255,0.59);
  background-color: @main-color;
  overflow: hidden;
  z-index: 2;

  opacity: 100%;  
}

.left-column-bg {
  background-repeat: no-repeat;
  background-size: cover;
  background-position: 25% 25%;
  
    opacity: .4; // up this value to contrast the cover image

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

.contact-container {
  margin-top: 30px;
  margin-bottom: 30px;
}

.txt-full-white {
  color: white;
}

.txt-multiline {
  margin-top: 30px;
  margin-bottom: 20px;
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

.section-headline {
  color: @main-color;
  display: inline-block;
  font-size: 1.3em;
  margin-left: 5px;
}
</style>
