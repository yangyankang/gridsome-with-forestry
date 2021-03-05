<template>
  <Layout>
    <div class="container">
      <Hero />
      <ProjectsGrid :projects="$page.projects.edges" />
    </div>
    <LatestJournals :journals="$page.journals.edges" />
  </Layout>
</template>
<page-query>
query {
  projects: allStrapiProject {
    edges {
      node {
        id
        title
        path
        date (format: "YYYY MM DD")
        project_bg_color
        project_fg_color
            
        categories {
            id
            tag
            name
          }
        thumbnail {
          url
        }
      }
    }
  }
   journals: allStrapiJournal {
    edges {
      node {
       id
       title
        date (format: "YYYY MM DD")
        timeToRead (format: "YYYY MM DD")
        path
        content
        author
        
      }
    }
  }
}
</page-query>

<script>
import Hero from "@/components/Hero";
import ProjectsGrid from "@/components/ProjectsGrid";
import LatestJournals from "@/components/LatestJournals";

export default {
  components: {
    Hero,
    ProjectsGrid,
    LatestJournals,
  },
  computed: {
    test() {
      return this.$page.projects.edges[0].node.id;
    },
  },
};
</script>
