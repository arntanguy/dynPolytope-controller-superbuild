# gram_savitzky_golay is already present when mc_rtc is built with ros support
if(NOT TARGET gram_savitzky_golay)
  AddProject(gram_savitzky_golay
    GITHUB jrl-umi3218/gram_savitzky_golay
    GIT_TAG origin/master
  )
endif()

AddProject(politopix
  GITHUB_PRIVATE Hugo-L3174/politopix
  GIT_TAG origin/libraryPort
)

AddProject(DCM_VRPTask
  GITHUB_PRIVATE Hugo-L3174/DCM_VRPTask
  GIT_TAG origin/main
  DEPENDS mc_rtc gram_savitzky_golay
)

AddProject(mc_dynamic_polytopes
  GITHUB_PRIVATE Hugo-L3174/mc_dynamic_polytopes
  GIT_TAG origin/main
  DEPENDS mc_rtc politopix
  APT_DEPENDENCIES libqhull-dev
)

AddProject(mc_force_shoe_plugin
  GITHUB_PRIVATE arntanguy/mc_force_shoe_plugin
  GIT_TAG origin/topic/Rewrite
  DEPENDS mc_rtc
)

AddProject(polytopeController
  GITHUB_PRIVATE Hugo-L3174/polytopeController
  GIT_TAG origin/master
  DEPENDS mc_rtc DCM_VRPTask mc_dynamic_polytopes mc_state_observation mc_force_shoe_plugin
)
