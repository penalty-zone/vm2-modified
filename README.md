# 魔改过的vm2


1. VM2 源码
    * VM2_INTERNAL_STATE_DO_NOT_USE_OR_PROGRAM_WILL_FAIL 找到引用的位置需要注释掉
        * VM2在执行时会默认修改你的代码，其中会插入  `${name}=${INTERNAL_STATE_NAME}.handleException(${name});`  
        * VM2_INTERNAL_STATE_DO_NOT_USE_OR_PROGRAM_WILL_FAIL 改个名字为 VM2_INTERNAL_STATE_DO_NOT_USE_OR_PROGRAM_WILL_FAIL_LcVM
          （避免window.VM2_INTERNAL_STATE_DO_NOT_USE_OR_PROGRAM_WILL_FAIL 检测）
        * acornWalkFull(ast, (node, state, type) => {  这段代码下面加个return;  （避免针对函数是否变动进行检测）