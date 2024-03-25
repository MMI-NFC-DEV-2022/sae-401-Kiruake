<template>
    <footer class="bg-white dark:bg-yellow-500 mt-32">
        <div class="mx-auto w-full max-w-screen-xl p-4 py-6 lg:py-8">
            <div class="md:flex md:justify-between">
              <div class="mb-6 md:mb-0">
                  <RouterLink to="/" class="flex items-center">
                            <a href="/" class="text-black text-lg font-semibold">ACFilms</a>
    
                  </RouterLink>
              </div>
              <div class="grid grid-cols-2 gap-8 sm:gap-6 sm:grid-cols-3">
                  <div>
                      <h2 class="mb-6 text-sm font-semibold text-gray-900 uppercase dark:text-black">Pages</h2>
                      <ul class="text-black dark:text-black font-medium">
                          <li class="mb-4">
                              <RouterLink to="/" class="hover:underline">Accueil</RouterLink>
                          </li>
                          <li>
                               <RouterLink to="/login-logout" class="hover:underline">Connexion</RouterLink>
                          </li>
                      </ul>
                  </div>
                  <div>
                      <h2 class="mb-6 text-sm font-semibold text-black uppercase dark:text-black">En savoir plus sur nous</h2>
                      <ul class="text-black dark:text-black font-medium">
                          <li class="mb-4">
                              <a href=" " class="hover:underline ">Github</a>
                          </li>
                          <li>
                              <a href="https://discord.gg/yGEuBtWa" class="hover:underline">Discord MMI</a>
                          </li>
                      </ul>
                  </div>
                  <div>
                      <h2 class="mb-6 text-sm font-semibold text-black uppercase dark:text-black">Mentions Légales</h2>
                      <ul class="text-black dark:text-black font-medium">
                          <li class="mb-4">
                              <RouterLink to="#" class="hover:underline">Politique de confidentialité</RouterLink>
                          </li>
                          <li>
                              <RouterLink to="#" class="hover:underline">Conditions d'utilisations</RouterLink>
                          </li>
                      </ul>
                  </div>
              </div>
          </div>
         
        </div>
    </footer>
    </template>
    