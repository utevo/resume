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
          <span class="uppercase">{{ person.contact.city }}, {{ person.contact.country }}</span>
        </p>
      </div>

      <div class="txt-multiline">{{ person.about }}</div>

      <div class="txt-multiline">{{ person.knowledge }}</div>

      <div class="contact-container">
        <a v-if="person.contact.email" :href="contactLinks.email" class="external-link">
          <i class="contact-icon material-icons">mail</i>
          <span class="block-marged txt-full-white">{{ person.contact.email }}</span>
        </a>

        <a v-if="person.contact.phone" :href="contactLinks.phone" class="external-link">
          <i class="contact-icon material-icon">mail</i>
          <span class="block-marged txt-full-white">{{ person.contact.phone }}</span>
        </a>

        <a v-if="person.contact.github" :href="contactLinks.github" class="external-link">
          <i class="contact-icon fa fa-github"></i>
          <span class="block-marged txt-full-white">{{ person.contact.github }}</span>
        </a>
      </div>

      <div class="skills-container">
        <span class="subheadline">Skills</span>
        <a
          v-for="(skill, index) in person.skills"
          :key="index"
          class="skill-item"
          :href="skill.url"
        >
          <i v-if="skill.iconClass" :class="'skill-icon ' + skill.iconClass"></i>
          <i v-if="skill.materialIcon" class="skill-icon material-icon">{{ skill.materialIcon }}</i>
          <span class="block-marged txt-full-white">{{ skill.name }}</span>
        </a>
      </div>

      <div class="hobbies-container">
        <span class="subheadline">Hobbies</span>
        <a
          v-for="(hobby, index) in person.hobbies"
          :key="index"
          class="hobby-item"
          :href="hobby.url"
        >
          <i v-if="hobby.iconClass" :class="'hobby-icon ' + hobby.iconClass"></i>
          <i v-if="hobby.materialIcon" class="hobby-icon material-icon">{{ hobby.materialIcon }}</i>
          <span class="block-marged txt-full-white">{{ hobby.name }}</span>
        </a>
      </div>
    </div>

    <div class="left-column-bg"></div>

    <div class="right-column">
      <div class="section experience-section">
        <div class="section-headline">
          <i class="material-icons small-icon">work</i>
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
          <i class="material-icons small-icon">school</i>
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
          <i class="material-icons small-icon">code</i>
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
          <i class="fa fa-heart small-icons"></i>
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
  height: 100%;
  padding: 30px;
  padding-top: 45px;
  text-align: left;

  color:rgba(255,255,255,0.59);
  background-color: @main-color;
  overflow: hiden;
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
</style>
