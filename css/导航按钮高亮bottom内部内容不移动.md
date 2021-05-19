只需要在外层容器写一个跟高亮时bottom宽度一样的bottom即可
 > .blog-header-nva {
                    height: 100%;
                    display: flex;
                    justify-content: center;
                    align-items: center;
                    border-bottom: 2px solid transparent;       //外层
                    &.active {
                        color: @scrollBar !important;
                        border-bottom: 2px solid @scrollBar;    //激活
                    }
 }
