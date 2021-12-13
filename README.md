### Hi there 👋

<!--
**mahdikhatirian1996/mahdikhatirian1996** is a ✨ _special_ ✨ repository because its `README.md` (this file) appears on your GitHub profile.

Here are some ideas to get you started:

- 🔭 I’m currently working on ...
- 🌱 I’m currently learning ...
- 👯 I’m looking to collaborate on ...
- 🤔 I’m looking for help with ...
- 💬 Ask me about ...
- 📫 How to reach me: ...
- 😄 Pronouns: ...
- ⚡ Fun fact: ...
--> <img src = "https://komarev.com/ghpvc/?username=mahdikhatirian1996&color=blue&style=flat-square">
<img src = "https://github-readme-stats.vercel.app/api?username=anuraghazra&theme=cobalt&show_icons=true">

const axios = require("axios");

const fetchWakatimeStats = async ({ username, api_domain, range }) => {
  try {
    const { data } = await axios.get(
      `https://${
        api_domain ? api_domain.replace(/\/$/gi, "") : "wakatime.com"
      }/api/v1/users/${username}/stats/${range || ''}?is_including_today=true`,
    );

    return data.data;
  } catch (err) {
    if (err.response.status < 200 || err.response.status > 299) {
      throw new Error(
        "Wakatime user not found, make sure you have a wakatime profile",
      );
    }
    throw err;
  }
};

module.exports = {
  fetchWakatimeStats,
};
